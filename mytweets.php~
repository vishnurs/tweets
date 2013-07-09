<?php
/* 
    Plugin Name: A short code plugin to retrieve the recent Tweets
    Plugin URI: 
    Description: A short code plugin for listing
    Author: Vishnu.R.S
    Version: 1.0 
    Author URI: http://vishnurs.com 
*/

require_once('TwitterAPIExchange.php');
function tweet_shortcode_handler( $atts, $content = null ) {
  
  $oauth_access_token = $atts['atoken'];
  $oauth_access_token_secret = $atts['asecret'];
  $consumer_key = $atts['ckey'];
  $consumer_secret = $atts['csecret'];
  $handle = $atts['handle'];
  $settings = array(
    		'oauth_access_token' => "$oauth_access_token",
    		'oauth_access_token_secret' => "$oauth_access_token_secret",
    		'consumer_key' => "$consumer_key",
    		'consumer_secret' => "$consumer_secret"
		);
  $url = 'https://api.twitter.com/1.1/statuses/user_timeline.json';
  $getfield = '?screen_name='.$handle.'&count=10';
  $requestMethod = 'GET';
  $twitter = new TwitterAPIExchange($settings);
  $val = $twitter->setGetfield($getfield)
             ->buildOauth($url, $requestMethod)
             ->performRequest();
  $tweets = json_decode($val);
  $i = 1;
  foreach ($tweets as $key=>$t)
  { 
    if(substr($t->text,0,4) == 'RT @')
      $str = $i.". ".substr($t->text,(strpos($t->text, ":")+1),strlen($t->text));// to remove RT in retweets
    else
	$str = $i.". ".$t->text;
	$i++;
	
	
	$parts = explode(" ", $str);
	for($j=0;$j<sizeof($parts);$j++)
	{
		
		$position1 = strpos($parts[$j],"http://");
		$position2= strpos($parts[$j],"https://");
		if($position1 !== FALSE || $position2 !== FALSE)
		{
			$position1 = strpos($parts[$j],"http://");
			$link = substr($parts[$j],$position1,(strlen($parts[$j])));
			$parts[$j] = "<a href='".$link."'>".$link.'</a>';
		}
	}
		
	$parts = implode(" ",$parts); //echo $parts;
	$string[] = $parts."<br/>";
	
  }
  foreach ($string as $t)
  { 
	echo $t."<br />";
  }
}
 add_shortcode( 'mytweets', 'tweet_shortcode_handler' );


?>