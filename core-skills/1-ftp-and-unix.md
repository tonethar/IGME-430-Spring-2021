# Skill #1 - FTP and Unix commands

## I. Overview
- Let's take one last look at `banjo.rit.edu` ...
- ... and we're going to give you a little Unix practice here
- Goals:
  - Post a PHP file to banjo using an FTP client (ex. [FileZilla](https://filezilla-project.org/))
  - Install these developer tools:
    - GitBash
    - [JSON Viewer](https://chrome.google.com/webstore/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh?hl=en-US)
  - `ssh` to banjo and practice a few basic Unix commands
 
<hr>

## II. PHP stuff we already did in IGME-330

### II-A. Upload *random-jokes.php* to `banjo.rit.edu`
- Post the **random-jokes.php** file below to banjo at `yourid/430/random-jokes.php` - if you have forgotten how to post files to banjo check out this page: https://github.com/tonethar/IGME-235-Shared/blob/master/notes/core-skills/ftp-upload-walkthrough.md

**random-jokes.php**

```php
<?php
	/*
		Name: get-jokes.php
		Description: Returns an array of random jokes in JSON format
		Author: 
		Last Modified: 
		Example usage: get-jokes.php?limit=3
	*/
	
	// I. define some constants
	define('MIN_LIMIT', 1); 
	define('MAX_LIMIT', 10); 
	
	
	// II. $jokes contains our data
	// this is an indexed array of associative arrays
	// the associative arrays are jokes -  they have an 'q' key and an 'a' key
	$jokes = [
		["q"=>"What do you call a very small valentine?","a"=>"A valen-tiny!"],
		["q"=>"What did the dog say when he rubbed his tail on the sandpaper?","a"=>"Ruff, Ruff!"],
		["q"=>"Why don't sharks like to eat clowns?","a"=>"Because they taste funny!"],
		["q"=>"What did the boy cat say to the girl cat?","a"=>"You're Purr-fect!"],
		["q"=>"What is a frog's favorite outdoor sport?","a"=>"Fly Fishing!"],
		["q"=>"I hate jokes about German sausages.","a"=>"Theyre the wurst."],
		["q"=>"Did you hear about the cheese factory that exploded in France?","a"=>"There was nothing left but de Brie."],
		["q"=>"Our wedding was so beautiful ","a"=>"Even the cake was in tiers."],
		["q"=>"Is this pool safe for diving?","a"=>"It deep ends."],
		["q"=>"Dad, can you put my shoes on?","a"=>"I dont think theyll fit me."],
		["q"=>"Can February March?","a"=>"No, but April May"],
		["q"=>"What lies at the bottom of the ocean and twitches?","a"=>"A nervous wreck."],
		["q"=>"Im reading a book on the history of glue.","a"=>"I just cant seem to put it down."],
		["q"=>"Dad, can you put the cat out?","a"=>"I didnt know it was on fire."],
		["q"=>"What did the ocean say to the sailboat?","a"=>"Nothing, it just waved."],
		["q"=>"What do you get when you cross a snowman with a vampire?","a"=>"Frostbite"]
	];
	
	
	// III. Sanitize the `limit` parameter to be sure that it is numeric, and is not too small or large
	$limit = MIN_LIMIT; // the default
	if(array_key_exists('limit', $_GET)){ // if there is a `limit` parameter in the query string
		$limit = $_GET['limit'];
		$limit = (int)$limit; // explicitly cast value to an integer
		$limit =  ($limit < 1) ? MIN_LIMIT : $limit; // PHP has a ternary operator too
		$limit =  ($limit > MAX_LIMIT) ? MAX_LIMIT : $limit; // PHP has a ternary operator too
	}
	
	
	// IV. Do a final check that there are enough jokes in the $jokes array
	if($limit > count($jokes)){
		$limit = count($jokes);
	}
	
	
	// V. get a random element of the $jokes array
	// there are a bunch more PHP array functions at: http://php.net/manual/en/ref.array.php
	// https://www.php.net/manual/en/function.shuffle.php
	// https://www.php.net/manual/en/function.array-push.php
	$randomKeys = array_keys($jokes); // creates an array of indexes - something like [0,1,2,3,4,5,6,7,...]
	shuffle($randomKeys); // randomizes the $randomKeys array - something like [1,5,3,2,0,8,4,7,6, ...]
	$randomKeys = array_slice($randomKeys, 0, $limit); // just get the first `n` number of indexes we need
	$randomJokes = []; // the random jokes will go here
	foreach($randomKeys as $key){ // loop through $randomKeys
 		array_push($randomJokes,$jokes[$key]); // add a random joke to the array
 	}
	
	
	// VI. Send HTTP headers
	// https://www.php.net/manual/en/function.header.php
	// DO THIS **BEFORE** you `echo()` the content!
	header('content-type:application/json');      			// tell the requestor that this is JSON
	header('Access-Control-Allow-Origin: *');     			// turn on CORS
	header('X-this-430-service-is-kinda-lame: true');   // a custom header 
	
	
	// VII. Send the content
	// json_encode() turns a PHP associative array into a string of well-formed JSON
	// https://www.php.net/manual/en/function.json-encode.php
	$string = json_encode($randomJokes);
	echo $string;

?>
```

- a working version is here: http://igm.rit.edu/~acjvks/courses/shared/430/php/get-jokes.php?limit=5


### II-B. Review

- Now open it up in the Chrome web browser to be sure that it works, it should appear something like the screenshot below
- If your screenshot is not as nicely formatted as mine, go download the [JSON Viewer](https://chrome.google.com/webstore/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh?hl=en-US) chrome extension now
- Open up the web inspector as I have done below

<hr>

## III. Discussion

- In 230/235/330, we used the `banjo.rit.edu` server to post web files (HTML/CSS/JS) and run simple server-side scripts utilizing PHP. Banjo has many other capabilities (via PHP and other languages) that we didn't explore such as the ability to store data on the server via SQLite, generate images via ??? and so on. With our banjo accounts we have been granted some access to the file system 


<hr>

## IV. Review Questions
 
<hr>

## V. Submission & Rubric (out of 10 points)
- In the myCourses dropbox, upload the two screenshots you took in part II. & part III. above
- Type the following into the comments field of the dropbox:
  - the link to your working version of **random-jokes.php** that is running on banjo
  - the answers to the review questions
- Rubric:
  - missing Screenshots (-5 each) 
  - no link, or link not working (-5)
  - Chrome JSON Viewer extension not utilized (-5) 


<hr><hr>

