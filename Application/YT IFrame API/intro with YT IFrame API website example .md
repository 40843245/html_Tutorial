# YT IFrame API (intro the example from the following website.)
First I paste the code from YT IFrame API website (which is available on the following link) as my example.

## Code

    <!DOCTYPE html>
      
      <html>
        <body>
          <!-- 1. The <iframe> (and video player) will replace this <div> tag. -->
            <div id="player"></div>

            <script>
                // 2. This code loads the IFrame Player API code asynchronously.
                var tag = document.createElement('script');
                tag.src = "https://www.youtube.com/iframe_api";
                var firstScriptTag = document.getElementsByTagName('script')[0];
                firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

                // 3. This function creates an <iframe> (and YouTube player)
                //    after the API code downloads.
                var player;
                function onYouTubeIframeAPIReady() 
                {
                    player = new YT.Player('player', 
                    {
                    height: '600',
                    width: '640',
                    videoId: 'M7lc1UVf-VE',
                    playerVars: {
                    'playsinline': 1
                    },
                    events: {
                    'onReady': onPlayerReady,
                    'onStateChange': onPlayerStateChange
                    }
                    });
                }

                // 4. The API will call this function when the video player is ready.
                function onPlayerReady(event) 
                {
                    event.target.playVideo();
                }

                // 5. The API calls this function when the player's state changes.
                //    The function indicates that when playing a video (state=1),
                //    the player should play for six seconds and then stop.
                var done = false;
                function onPlayerStateChange(event) 
                {
                    if (event.data == YT.PlayerState.PLAYING && !done) 
                    {
                        setTimeout(stopVideo, 6000);
                        done = true;
                    }
                }
                function stopVideo() 
                {
                    player.stopVideo();
                }
            </script>
        </body>
    </html>

## Intro

### 1. Event and callback functions
    
    onYouTubeIframeAPIReady(), onPlayerReady(event) and onPlayerStateChange(event) are callback functions
    
part 1: For onYouTubeIframeAPIReady()

It is a special callback function. It is a built-in function YT IFrame API that is invoked iff the YT frame API is ready (at the beginning of executing this file).

Here, we override the callback function.
     

part 2:For onPlayerReady(event) and onPlayerStateChange(event) for events, they are defined as follows which indicates that

    events: {
                    'onReady': onPlayerReady,
                    'onStateChange': onPlayerStateChange
             }
          
 once onReady event is triggered, the function onPlayerReady(event) was called
 
 and once onStateChange event is triggered, the function onPlayerStateChange(event) was called.
 
 When the YT video is ready to play, the onReady signal is send and onReady event is triggered, thus invoking  onPlayerReady(event) 
 
 and  when the YT video status is changed, the onStateChange signal is send and onStateChange event is triggered, thus invoking  onPlayerStateChange(event).
 
 
 ### 2. The details of onPlayerStateChange(event)
 
 #### Correct code (code1)
 
 For the piece of the code,
 
 it invokes stopVideo() whichh stops playing the video after six seconds at first execution of onPlayerStateChange.
                
                //code1
                var done = false;
                function onPlayerStateChange(event) 
                {
                    if (event.data == YT.PlayerState.PLAYING && !done) 
                    {
                        setTimeout(stopVideo, 6000);
                        done = true;
                    }
                }
 
#### Code and its explanation that lead to unexpected results

In the following peices of code, one will get unexpected results  due to compiler errors or the logical error.

##### code 2.
Consider the following code.

                //code2
                function onPlayerStateChange(event) 
                {
                    if (event.data == YT.PlayerState.PLAYING && !done) 
                    {
                        setTimeout(stopVideo, 6000);
                        done = true;
                    }
                }

In the piece of code, code2, the done is accessed at the if-statement before declaration. It will cause unexpected result dues to compiler error.

##### code3
Also, the following code will lead unexpected results.

                //code3
                var done;
                function onPlayerStateChange(event) 
                {
                    if (event.data == YT.PlayerState.PLAYING  && !done) 
                    {
                        setTimeout(stopVideo, 6000);
                        done=true;
                    }
                }

In the piece of code, code3, it seems fine, but there are logical problem.

Since done has NOT been assigned yet, done is undefined. Thus, !done may NOT be true. It will cause unexpected result dues to logical error.

##### code4
Also, the following code will lead unexpected results.

                //code4
                var done = false;
                function onPlayerStateChange(event) 
                {
                    if (event.data == YT.PlayerState.PLAYING  && !done) 
                    {
                        setTimeout(stopVideo, 6000);
                    }
                }

In the piece of code, code4, it seems fine, but there are logical problem.

Since done will never be assigned to true, done is always false. Once the onPlayerStateChange is invoked and event.data == YT.PlayerState.PLAYING is true, 

the statement setTimeout(stopVideo, 6000); will be executed.

code4 is equivalent to code4.2 in this example.

                //code4.2
                function onPlayerStateChange(event) 
                {
                    if (event.data == YT.PlayerState.PLAYING) 
                    {
                        setTimeout(stopVideo, 6000);
                    }
                }

which may execute the statement setTimeout(stopVideo, 6000); many times. 

(In code1, the statement will be executed at most once.)

##### code5
 
                //code5
                function onPlayerStateChange(event) 
                {
                    var done = false;
                    if (event.data == YT.PlayerState.PLAYING && !done) 
                    {
                        setTimeout(stopVideo, 6000);
                        done = true;
                    }
                }
                
The code5 will also led to unexpected result. Since before the if-statement, done is always set to be true.

It is equivalent to code4 and code4.2 .

### 3. Code and its intro  for the creating YT.Player object 

            <div id="player"></div>

            <script>
                // 2. This code loads the IFrame Player API code asynchronously.
                var tag = document.createElement('script');
                tag.src = "https://www.youtube.com/iframe_api";
                var firstScriptTag = document.getElementsByTagName('script')[0];
                firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

                // 3. This function creates an <iframe> (and YouTube player)
                //    after the API code downloads.
                var player;
                function onYouTubeIframeAPIReady() 
                {
                    player = new YT.Player('player', 
                    {
                    height: '600',
                    width: '640',
                    videoId: 'M7lc1UVf-VE',
                    playerVars: 
                        {
                        'playsinline': 1
                        }
                        ,
                    events: 
                    {
                    'onReady': onPlayerReady,
                    'onStateChange': onPlayerStateChange
                    }
                    });
                }
                
1. For the callback function  onYouTubeIframeAPIReady(), we have discussed in part 1 of 1.

2. For the first argument of YT.player, it determines which element is used for the newly-created object by id.

#### NOTE
NOTE that 

    1) It must takes the element with <div> tags.
    
    2) The value of first argument of YT.player must match the value of the attribute id of the element one used.
    
3. For the second argument of YT.player, it determines the basic info of the object.

#### NOTE
The second argument of YT.player must be a dictionary.

height

    height refers the height for the element holds.

width

    width refers the width for the element holds.

videoId

    videoId refers the videoId it will be played.
    
    It will play the video with url "https://www.youtube.com/watch?v=" + videoId .
 
playerVars

    I don't know. I'm NOT an expertise.

events

    events contains all infos. Once a specific event is triggered then the corresponding callback function will be executed.
   
    More details about it on the part 2 of 1.
    
#### NOTE
NOTE that events must corresponding to a dictionary.
                
## Ref

For more details, methods and attribute of YT.Player, visit on the following website.

Google Docs

https://developers.google.com/youtube/iframe_api_reference
