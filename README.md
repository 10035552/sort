<!DOCTYPE html>
<script>var __pbpa = true;</script><script>var translated_warning_string = 'Warning: Never enter your Tumblr password unless \u201chttps://www.tumblr.com/login\u201d\x0ais the address in your web browser.\x0a\x0aYou should also see a green \u201cTumblr, Inc.\u201d identification in the address bar.\x0a\x0aSpammers and other bad guys use fake forms to steal passwords.\x0a\x0aTumblr will never ask you to log in from a user\u2019s blog.\x0a\x0aAre you absolutely sure you want to continue?';</script><script type="text/javascript" language="javascript" src="http://assets.tumblr.com/assets/scripts/pre_tumblelog.js?_v=66ac555bc5745ebe20abdae7cbc40704"></script>
<!doctype HTML>
<link rel="shortcut icon" href="http://sv.tinypic.com?ref=qq68e9">
 
<html>
 
<head prefix="og: http://ogp.me/ns# fb: http://ogp.me/ns/fb# blog: http://ogp.me/ns/blog#">
 
<meta http-equiv="Content-Type" content="text/html; charset=Shift_JIS">
 
<meta http-equiv="Content-Style-Type" content="text/css">
 
<meta http-equiv="Content-Script-Type" content="text/javascript">
 
<script type="text/javascript">
 
<!--
 
var namMember = new Array(
 
"Still I Luv You",
 
"Daddy's Girl",
 
"DRAMA",

"MEDUSA",

"Paper Plane",

"Youth",

"Coming Home",

"얼어있는 길거리에 잠시라도 따듯한 햇빛이 내리길 Camellia",

"Coming Home (Acoustic English Ver.)",

"Get Away",

"DAMAGE",

"My Way",

"Double Dare",

"Deja Vu",

"DOMINO",

"Ready Or Not",

"ME=(NANEUN)",

"Cherry on Top",

"밤공기 Night Stroll",

"DASH!",

"RE=LOAD",

"Make It New",

"Don't Go Back",

"Lights On",

"TICK TOCK",

"Vindicated",

"Try",

"MBTI",

"Tasty",

"Paradise (사장돌 마트 OST)",

"I luv you Merry Christmas"
 
);
 
 
 
//*********************************************************
 
 
 
var lstMember = new Array();
 
var parent = new Array();
 
var equal = new Array();
 
var rec = new Array();
 
var cmp1,cmp2;
 
var head1,head2;
 
var nrec;
 
 
 
var numQuestion;
 
var totalSize;
 
var finishSize;
 
var finishFlag;
 
 
 
//The initialization of the variable+++++++++++++++++++++++++++++++++++++++++++++
 
function initList(){
 
var n = 0;
 
var mid;
 
var i;
 
 
 
//The sequence that you should sort
 
lstMember[n] = new Array();
 
for (i=0; i<namMember.length; i++) {
 
lstMember[n][i] = i;
 
}
 
parent[n] = -1;
 
totalSize = 0;
 
n++;
 
 
 
for (i=0; i<lstMember.length; i++) {
 
//And element divides it in two/more than two
 
//Increase divided sequence of last in first member
 
if(lstMember[i].length>=2) {
 
mid = Math.ceil(lstMember[i].length/2);
 
lstMember[n] = new Array();
 
lstMember[n] = lstMember[i].slice(0,mid);
 
totalSize += lstMember[n].length;
 
parent[n] = i;
 
n++;
 
lstMember[n] = new Array();
 
lstMember[n] = lstMember[i].slice(mid,lstMember[i].length);
 
totalSize += lstMember[n].length;
 
parent[n] = i;
 
n++;
 
}
 
}
 
 
 
//Preserve this sequence
 
for (i=0; i<namMember.length; i++) {
 
rec[i] = 0;
 
}
 
nrec = 0;
 
 
 
//List that keeps your results
 
//Value of link initial
 
// Value of link initial
 
for (i=0; i<=namMember.length; i++) {
 
equal[i] = -1;
 
}
 
 
 
cmp1 = lstMember.length-2;
 
cmp2 = lstMember.length-1;
 
head1 = 0;
 
head2 = 0;
 
numQuestion = 1;
 
finishSize = 0;
 
finishFlag = 0;
 
}
 
 
 
//&#12522;&#12473;&#12488;&#12398;&#12477;&#12540;&#12488;+++++++++++++++++++++++++++++++++++++++++++
 
//flag&#65306;Don't know characters
 
// -1&#65306;Chose the left
 
// 0&#65306;Tie
 
// 1&#65306;Chose the right
 
function sortList(flag){
 
var i;
 
var str;
 
 
 
//rec preservation
 
if (flag<0) {
 
rec[nrec] = lstMember[cmp1][head1];
 
head1++;
 
nrec++;
 
finishSize++;
 
while (equal[rec[nrec-1]]!=-1) {
 
rec[nrec] = lstMember[cmp1][head1];
 
head1++;
 
nrec++;
 
finishSize++;
 
}
 
}
 
else if (flag>0) {
 
rec[nrec] = lstMember[cmp2][head2];
 
head2++;
 
nrec++;
 
finishSize++;
 
while (equal[rec[nrec-1]]!=-1) {
 
rec[nrec] = lstMember[cmp2][head2];
 
head2++;
 
nrec++;
 
finishSize++;
 
}
 
}
 
else {
 
rec[nrec] = lstMember[cmp1][head1];
 
head1++;
 
nrec++;
 
finishSize++;
 
while (equal[rec[nrec-1]]!=-1) {
 
rec[nrec] = lstMember[cmp1][head1];
 
head1++;
 
nrec++;
 
finishSize++;
 
}
 
equal[rec[nrec-1]] = lstMember[cmp2][head2];
 
rec[nrec] = lstMember[cmp2][head2];
 
head2++;
 
nrec++;
 
finishSize++;
 
while (equal[rec[nrec-1]]!=-1) {
 
rec[nrec] = lstMember[cmp2][head2];
 
head2++;
 
nrec++;
 
finishSize++;
 
}
 
}
 
 
 
//Processing after finishing with one list
 
if (head1<lstMember[cmp1].length && head2==lstMember[cmp2].length) {
 
//List the remainder of cmp2 copies, list cmp1 copies when finished scanning
 
while (head1<lstMember[cmp1].length){
 
rec[nrec] = lstMember[cmp1][head1];
 
head1++;
 
nrec++;
 
finishSize++;
 
}
 
}
 
else if (head1==lstMember[cmp1].length && head2<lstMember[cmp2].length) {
 
//List the remainder of cmp1 copies, list cmp2 copies when finished scanning
 
while (head2<lstMember[cmp2].length){
 
rec[nrec] = lstMember[cmp2][head2];
 
head2++;
 
nrec++;
 
finishSize++;
 
}
 
}
 
 
 
//When it arrives at the end of both lists
 
//Update a pro list
 
if (head1==lstMember[cmp1].length && head2==lstMember[cmp2].length) {
 
for (i=0; i<lstMember[cmp1].length+lstMember[cmp2].length; i++) {
 
lstMember[parent[cmp1]][i] = rec[i];
 
}
 
lstMember.pop();
 
lstMember.pop();
 
cmp1 = cmp1-2;
 
cmp2 = cmp2-2;
 
head1 = 0;
 
head2 = 0;
 
 
 
//Initialize the rec before performing the new comparison
 
if (head1==0 && head2==0) {
 
for (i=0; i<namMember.length; i++) {
 
rec[i] = 0;
 
}
 
nrec = 0;
 
}
 
}
 
 
 
if (cmp1<0) {
 
str = "battle #"+(numQuestion-1)+"<br>"+Math.floor(finishSize*100/totalSize)+"% sorted.";
 
document.getElementById("battleNumber").innerHTML = str;
 
 
 
showResult();
 
finishFlag = 1;
 
}
 
else {
 
showImage();
 
}
 
}
 
 
 
//The results+++++++++++++++++++++++++++++++++++++++++++++++
 
//&#38918;&#20301;=Rank/Grade/Position/Standing/Status
 
//&#21517;&#21069;=Identification term
 
function showResult() {
 
var ranking = 1;
 
var sameRank = 1;
 
var str = "";
 
var i;
 
 
 
str += "<table style=\"width:200px; font-size:18px; line-height:120%; margin-left:auto; margin-right:auto; border:1px solid #000; border-collapse:collapse\" align=\"center\">";
 
str += "<tr><td style=\"color:#ffffff; background-color:#e097d9; text-align:center;\">rank<\/td><td style=\"color:#ffffff; background-color:#e097d9; text-align:center;\">options<\/td><\/tr>";
 
 
 
for (i=0; i<namMember.length; i++) {
 
str += "<tr><td style=\"border:1px solid #000; text-align:center; padding-right:5px;\">"+ranking+"<\/td><td style=\"border:1px solid #000; padding-left:5px;\">"+namMember[lstMember[0][i]]+"<\/td><\/tr>";
 
if (i<namMember.length-1) {
 
if (equal[lstMember[0][i]]==lstMember[0][i+1]) {
 
sameRank++;
 
} else {
 
ranking += sameRank;
 
sameRank = 1;
 
}
 
}
 
}
 
str += "<\/table>";
 
 
 
document.getElementById("resultField").innerHTML = str;
 
}
 
 
 
//Indicates two elements to compare+++++++++++++++++++++++++++++++++++
 
function showImage() {
 
var str0 = "battle #"+numQuestion+"<br>"+Math.floor(finishSize*100/totalSize)+"% sorted.";
 
var str1 = ""+toNameFace(lstMember[cmp1][head1]);
 
var str2 = ""+toNameFace(lstMember[cmp2][head2]);
 
 
 
document.getElementById("battleNumber").innerHTML = str0;
 
document.getElementById("leftField").innerHTML = str1;
 
document.getElementById("rightField").innerHTML = str2;
 
 
 
numQuestion++;
 
}
 
 
 
//Convert numeric value into a name (emoticon)+++++++++++++++++++++++++++++++
 
function toNameFace(n){
 
var str = namMember[n];
 
 
 
/*
 
str += '<br />';
 
switch(n) {
 
//case -1 Because it is a sample, delete it
 
case -1: str+=""; break;
 
}*/
 
return str;
 
}
 
//-->
 
</script>
 
<style type="text/css">
 
<!--
 
#mainTable{
 
font-size: 19px;
 
font-family: 'Times New Roman', serif;
 
text-align: center;
 
vertical-align: middle;
 
width: 410px;
 
margin-left: auto;
 
margin-right: auto;
 
border-collapse: separate;
 
border-spacing: 10px 5px;
 
}
 
#leftField{
 
width: 120px;
 
height: 150px;
 
border: 1px solid #000;
 
cursor: pointer;
 
}
 
#rightField{
 
width: 120px;
 
height: 150px;
 
border: 1px solid #000;
 
cursor: pointer;
 
}
 
.middleField{
 
width: 120px;
 
height: 70px;
 
border: 1px solid #000;
 
cursor: pointer;
 
}
 
a{
 
color: #e097d9;
 
text-decoration : none;
 
}
 
a:hover{
 
color: #8f8f8f;
 
}
 
body {
 
width: 600px;
 
margin: 0 auto;
 
font-family: 'Times New Roman', erif;
 
}
 
-->
 
</style>
 
 
<!-- BEGIN TUMBLR FACEBOOK OPENGRAPH TAGS --><!-- If you'd like to specify your own Open Graph tags, define the og:url and og:title tags in your theme's HTML. --><!-- Read more: http://ogp.me/ --><meta property="fb:app_id" content="48119224995" /><meta property="og:site_name" content="" /><meta property="og:title" content="Not Found" /><meta property="og:url" content="" /><meta property="og:description" content="The URL you requested could not be found." /><meta property="og:determiner" content="a" /><meta property="og:type" content="tumblr-feed:entry" /><meta property="og:image" content="http://assets.tumblr.com/images/og/text_200.png" /><!-- END TUMBLR FACEBOOK OPENGRAPH TAGS -->
 
 
<!-- TWITTER TAGS --><meta charset="utf-8"><meta name="twitter:card" content="summary" /><meta name="twitter:description" content="The URL you requested could not be found." /><meta name="twitter:title" content="Not Found" /><meta name="twitter:url" content="" /><meta name="twitter:site" content="tumblr" /><meta name="twitter:app:name:iphone" content="Tumblr" /><meta name="twitter:app:name:ipad" content="Tumblr" /><meta name="twitter:app:name:googleplay" content="Tumblr" /><meta name="twitter:app:id:iphone" content="305343404" /><meta name="twitter:app:id:ipad" content="305343404" /><meta name="twitter:app:id:googleplay" content="com.tumblr" /><meta name="twitter:app:url:iphone" content="tumblr://x-callback-url/blog?blogName=roosterteethcs&amp;postID=&amp;referrer=twitter-cards" /><meta name="twitter:app:url:ipad" content="tumblr://x-callback-url/blog?blogName=roosterteethcs&amp;postID=&amp;referrer=twitter-cards" /><meta name="twitter:app:url:googleplay" content="tumblr://x-callback-url/blog?blogName=roosterteethcs&amp;postID=&amp;referrer=twitter-cards" />
 
<script src="http://assets.tumblr.com/assets/scripts/tumblelog.js?_v=a9e2d0b0ade5958a1a2a936adf448061"></script>
<meta http-equiv="x-dns-prefetch-control" content="off"/>
</head>
<link href='http://fonts.googleapis.com/css?family=Josefin+Slab:600' rel='stylesheet' type='text/css'>
 
<body text="#000000" bgcolor="#ffffff" link="#e097d9" vlink="#e097d9" alink="#79a2c9">
 
 
 
<p class="instructions">
<center><br /><br />
<b>just b song sorter</b><br /><br>choose which just b song you like better in each battle to get an accurate list of <br />your favorite songs from them.<br />note: hitting 'no opinion' or 'I like both' frequently will negatively affect your results.<br /><br /></center>
 
 
 
</p>
 
 
 
<table id="mainTable" align="center">
 
<tbody><tr>
 
<td id="battleNumber" colspan="3" style="padding-bottom: 10px;" style="text-align:center;"><b>battle #1<br>0% sorted.</b></td>
 
</tr>
 
<tr>
 
<td id="leftField" onclick="if(finishFlag==0) sortList(-1);" rowspan="2" style="text-align:center;"></td>
 
<td class="middleField" onclick="if(finishFlag==0) sortList(0);" style="text-align:center;">
 
I like both
 
</td>
 
<td id="rightField" onclick="if(finishFlag==0) sortList(1);" rowspan="2"style="text-align:center;"></td>
 
</tr>
 
<tr>
 
<td class="middleField" onclick="if(finishFlag==0) sortList(0);"style="text-align:center;">
 
no opinion
 
</td>
 
</tr>
 
</tbody></table>
 
<br><br>
 
<div id="resultField" style="text-align: center;">
 
<br>
 
</div>
 
<script type="text/javascript">
 
<!--
 
initList();
 
showImage();
 
//-->
 
 
</script>
<p class="other">
<center><small><br /><br />by tulip @_10035552<br /><br/><a href="http://biasorter.tumblr.com/">(code by biasorter)</a>
</small></center></small>
</p>
 
<!-- BEGIN TUMBLR CODE --><iframe id="tumblr_controls" width="1" height="1" frameborder="0" scrolling="no" style="position:absolute; z-index:2147483647; top:0; right:0; border:0; background-color:transparent; overflow:hidden; " src="http://assets.tumblr.com/assets/html/iframe/o.html?_v=dddebe193046ef922006b33d60687b05#src=http%3A%2F%2Froosterteethcs.tumblr.com%2Fask&amp;lang=en_US&amp;name=roosterteethcs&amp;avatar=http%3A%2F%2Fassets.tumblr.com%2Fimages%2Fdefault_avatar%2Fpyramid_open_64.png&amp;title=rt+character+sorter&amp;url=http%3A%2F%2Froosterteethcs.tumblr.com%2F&amp;page_slide=slide"></iframe><div id="teaser_iframe_container" style="display:none;"><iframe scrolling="no" frameborder="0" src="http://www.tumblr.com/assets/html/iframe/teaser.html?_v=0334cdd0135fa4ea13587cd37c2dcf98#src=http%3A%2F%2Froosterteethcs.tumblr.com%2Fask&amp;lang=en_US&amp;name=roosterteethcs&amp;avatar=http%3A%2F%2Fassets.tumblr.com%2Fimages%2Fdefault_avatar%2Fpyramid_open_64.png&amp;title=rt+character+sorter&amp;url=http%3A%2F%2Froosterteethcs.tumblr.com%2F&amp;page_slide=slide" id="teaser_iframe" width="1" height="1"></iframe></div><!--[if IE]><script type="text/javascript">document.getElementById('tumblr_controls').allowTransparency=true;</script><![endif]--><iframe onload="javascript:this.contentWindow.postMessage(['tick_google_analytics', '/ask?route=404_page'].join(';'), this.src.split('/analytics.html')[0]);  COMSCORE = true;this.contentWindow.postMessage('enable_comscore;' + window.location, this.src.split('/analytics.html')[0]);" src="http://assets.tumblr.com/analytics.html?9bbb9e7732da937858cd0531689c20b1" scrolling="no" width="1" height="1" frameborder="0" style="background-color:transparent; overflow:hidden; position:absolute; top:0; left:0 z-index:9999;" id="ga_target"></iframe><script type="text/javascript">
      var _qevents = _qevents || [];
 
      (function() {
       var elem = document.createElement('script');
 
       elem.src = (document.location.protocol == "https:" ? "https://secure" : "http://edge") + ".quantserve.com/quant.js";
       elem.async = true;
       elem.type = "text/javascript";
       var scpt = document.getElementsByTagName('script')[0];
       scpt.parentNode.insertBefore(elem, scpt);
      })();
    </script><script type="text/javascript">
        _qevents.push( { qacct: 'p-19UtqE8ngoZbM' } );
    </script><noscript><div style="display: none;"><img src="//pixel.quantserve.com/pixel/'p-19UtqE8ngoZbM'.gif" height="1" width="1" alt="Quantcast"/></div></noscript><script type="text/javascript">!function(s){s.src='http://www.tumblr.com/impixu?T=1389854658&J=eyJ0eXBlIjoidXJsIiwidXJsIjoiaHR0cDpcL1wvcm9vc3RlcnRlZXRoY3MudHVtYmxyLmNvbVwvYXNrIiwicmVxdHlwZSI6MCwicm91dGUiOiI0MDRfcGFnZSJ9&U=GJPMNFPHIN&K=745811f0e9615242e744b26218c2e56a6c6b184a1315e6c9e9e871a0c242e3ab&R=http%3A%2F%2Froosterteethcs.tumblr.com%2F'.replace(/&R=[^&$]*/,'').concat('&R='+escape(document.referrer)).slice(0,2000).replace(/%.?.?$/,'');}(new Image());</script><noscript><img style="position:absolute;z-index:-3334;top:0px;left:0px;visibility:hidden;" src="http://www.tumblr.com/impixu?T=1389854658&J=eyJ0eXBlIjoidXJsIiwidXJsIjoiaHR0cDpcL1wvcm9vc3RlcnRlZXRoY3MudHVtYmxyLmNvbVwvYXNrIiwicmVxdHlwZSI6MCwicm91dGUiOiI0MDRfcGFnZSIsIm5vc2NyaXB0IjoxfQ==&U=GJPMNFPHIN&K=c7a8ec33be24dcae3b08d0ffc26af0508ef65362a18101b8963123d054b7f79e&R=http%3A%2F%2Froosterteethcs.tumblr.com%2F"></noscript><script type="text/javascript" src="http://l.yimg.com/ss/rapid-3.9.js"></script><script>
                    (function(YAHOO) {
                        if (YAHOO) {
                            YAHOO.i13n.beacon_server = 'nol.yahoo.com';
                            var keys = { pd:'404_page', _li:0, i_rad:0, i_strm:0 };
                            YAHOO.rapid = new YAHOO.i13n.Rapid({spaceid:1197719233, oo:1, client_only:1, yql_enabled:false, keys:keys});
                        }
                    })(window.YAHOO);
                </script><!-- END TUMBLR CODE -->
 
</body>
 
</html>
