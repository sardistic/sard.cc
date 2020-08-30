
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
<script src="https://github.com/devteaminc/Last.fm-Now-Playing-Widget/blob/master/jquery.lastfmnowplaying.js"></script>


<script type="text/template" id="lastFmWidget">
	<div>{ track.artist }</div>
	<div>{ track.title }</div>
	<div>{ track.album }</div>
	<img src="{ track.image.medium }">
</script>

/**

<script>
	var lastfmData = {
  baseURL:
    "https://ws.audioscrobbler.com/2.0/?method=user.getrecenttracks&user=",
  // Your Last.fm Username
  user: "coldhunter",
  // Your API key
  api_key: "1a02967e3f034ad101153c030e8d2b6a",
  additional: "&format=json&limit=1"
};

var getSetLastFM = function() {
  $.ajax({
    type: "GET",
    url:
      lastfmData.baseURL +
      lastfmData.user +
      "&api_key=" +
      lastfmData.api_key +
      lastfmData.additional,
    dataType: "json",
    success: function(resp) {
      var recentTrack = resp.recenttracks.track[0];
      var formatted =
        "<img src='https://i.imgur.com/EgWjJry.png'>" + recentTrack.name;
      $("a#tracktitle")
        .html(formatted)
        .attr("href", recentTrack.url)
        .attr("title", recentTrack.name + " by " + recentTrack.artist["#text"])
        .attr("target", "_blank");

      var artistFormatted =
        "<img src='https://i.imgur.com/fae5XZA.png'>" +
        recentTrack.artist["#text"];
      $("a#trackartist")
        .html(artistFormatted)
        .attr("title", "Artist : " + recentTrack.artist["#text"]);
      $("img#trackart").attr("src", recentTrack.image[2]["#text"]);
    },
    error: function(resp) {
      $("a#tracktitle").html(
        "<img src='https://i.imgur.com/EgWjJry.png'>" + "Silence!"
      );
      $("img#trackart").attr("src", "https://i.imgur.com/Q6cCswP.jpg");
      var artistFormatted =
        "<img src='https://i.imgur.com/fae5XZA.png'>Prashant Shrestha";
      $("a#trackartist")
        .html(artistFormatted)
        .attr("href", "www.prashant.me/");
    }
  });
};

// Get the new one.
getSetLastFM();
// Start the countdown.
setInterval(getSetLastFM, 10 * 1000);
</script>

@import url("https://fonts.googleapis.com/css?family=Source+Sans+Pro");

$globalFontSize: 13px;
$globalFontFamily: "Source Sans Pro", sans-serif;
$globalBorderRadius: 3px;

@mixin border-left-radius($radius) {
  -webkit-border-top-left-radius: $radius;
  -moz-border-top-left-radius: $radius;
  -ms-border-top-left-radius: $radius;
  -o-border-top-left-radius: $radius;
  border-top-left-radius: $radius;

  -webkit-border-bottom-left-radius: $radius;
  -moz-border-bottom-left-radius: $radius;
  -ms-border-bottom-left-radius: $radius;
  -o-border-bottom-left-radius: $radius;
  border-bottom-left-radius: $radius;
}

body {
  padding: 0;
  margin: 0;

  .nowplayingcard {
    min-width: 200px;
    max-width: 20%;
    margin: 0 auto;
    margin-top: 5%;
    font-family: $globalFontFamily;
    font-size: $globalFontSize;

    .nowplayingcontainer-inner {
      width: 100%;
      box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
      transition: 0.3s;
      display: inline-block;
      @include border-left-radius($globalBorderRadius);

      &:hover {
        box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
      }

      img#trackart {
        max-width: 30%;
        float: left;
        left: 0;
        @include border-left-radius($globalBorderRadius);
      }

      .trackInfo {
        width: 70%;
        float: left;
        display: block;

        a {
          max-width: 90%;
          display: block;
          font-size: 14px;
          text-align: left;
          text-decoration: none;
          vertical-align: middle;
          overflow: hidden;
          white-space: nowrap;
          text-overflow: ellipsis;

          &:nth-child(odd) {
            img {
              width: 15px;
              height: 15px;
              vertical-align: middle;
              margin: -2% 3px 0 0;
            }

            color: black;
            font-weight: bold;
            vertical-align: middle;
            line-height: 15px;
            letter-spacing: 0.2px;
            padding: 10% 0 0 5%;
          }

          &:nth-child(even) {
            img {
              width: 15px;
              height: 15px;
              vertical-align: middle;
              margin: -2% 3px 0 0;
            }

            color: gray;
            font-size: $globalFontSize - 1px;
            letter-spacing: 0.1px;
            padding: 5% 0 0 5%;
          }
        }
      }
    }
  }
}

<div class="nowplayingcard">
    <div class="nowplayingcontainer-inner">
        <img id="trackart" src="#">
        <div class="trackInfo">
            <a id="tracktitle"></a>
            <a href="#" id="trackartist"></a>
        </div>
    </div>
</div>
