//jangan lupa subscribe youtube ShareID
function statsTitle() {
  
  //Video info video target
  var videoID = 'raszHvtAvGk'; //https://youtu.be/pL4TLEbIsAA
  var part = 'snippet,statistics';
  var params = {'id': videoID};
  var response = YouTube.Videos.list(part, params);
  var video = response.items[0];
  
  //info channel anda
  var channelID = 'UCS3mfHRgF2-xX20GgBtj8dQ' ; //https://www.youtube.com/channel/UCxaaULLk6UCnRl5VKRc7G0A
  var part2 = 'snippet,contentDetails,statistics';
  var params2 = {'id': channelID};
  var response2 = YouTube.Channels.list(part2, params2);
  var channel = response2.items[0];

  //Video title variables
  var videoViews = video.statistics.viewCount;
  var videoLikes = video.statistics.likeCount;
  var videoDislikes = video.statistics.dislikeCount;
  var videoComments = video.statistics.commentCount;
  var channelSubs = channel.statistics.subscriberCount;
  var channelVideos = channel.statistics.videoCount;
  var channelViews = channel.statistics.viewCount;
  
  //Set Video Title incoportating "Video title variables"
  //contoh
  //var videoTitle = 'This channel has ' + channelSubs + ' subscribers, ' + channelVideos + ' videos and ' + channelViews + ' views!';
  //var videoTitle = 'judul  ' + videoViews + ' views, ' + videoLikes + ' likes, ' + videoDislikes + ' dislikes, and ' + videoComments + ' comments!';
  var videoTitle = 'vudeo ini di tonton ' + videoViews + ' kali';
  
  //Update youtube video
  video.snippet.title = videoTitle;
  try
  {
        YouTube.Videos.update(video, part);
  }
  catch(e){}
}
