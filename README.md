# jquery-rss-feeder

The purpose of this code is to create a CSS driven vertical ticking scroll of an RSS feed from a Twitter page (or anywhere actualy including a blog). It not only scrolls vertically, but will stop when you hover over it.

### Version
1.0.0

### Tech

jquery-rss-feeder uses a number of open source projects to work properly:

  - jQuery.com 
  - feed.informer.com - Converts the RSS feed to HTML.
  - twitrss.me - Converts the Twitter Page to and RSS feed.

### Development

Want to contribute? Great!


### To Dos

  - Write Tests
  - Rethink Github Save
  - Add Code Comments
  
### Details

Basically the RSS feed is being converted by Feed Informer to HTML using the template (see below). I am importing that template into blogObject and then writing that object to the console. 

The main code was written in classic ASP because that is what we use on our current system.  ASP has some very big limitations, but in the end, the solution was very simple.


####ASP (vbScript)
----------------------------------------------

```
<%
  On Error Resume Next
  dim blogObject
  set blogObject = CreateObject("MSXML2.XMLHTTP")
  Call blogObject.Open("GET", "http://feed.informer.com/widgets/1PE6GMRN1P.html", false)
  Call blogObject.Send()
  Response.Write(blogObject.responseText)
  Response.Flush()
  set blogObject = nothing
%>
```

####Feed Informer Template
----------------------------------------------

Just create your own custom widget in Feed Informer then put this template in the Header, Per-Item and Footer and save it. It will create the HTML code for the ASP code I am using above. 

Feel free to hit preview to see the actually output. You can use this same custom widget code for any RSS feed. 

Header Template:
```
<div class="news-wrap">
  <div class="twitter-news marquee">
```

Per-Item Template:
```
    <div class="twitter-news-item marquee-item" onclick="window.open('%URL%');"><span></span>
      <div><a href="%URL%" title="%DESCRIPTIONPLAIN,150%" target="_blank">%DESCRIPTIONPLAIN,150%</a></div>
    </div>
```

Footer Template:
```
  </div>
</div>
```

----------------------------------------------

###Additional Info

The included HTML file in this project is just an exmaple of what the RSS feed will look like after the ASP has imported and parced the RSS feed to HTML. I included it only because I helps when to see when styling the CSS and working with the JQuery code. However, the ASP is actually able to create the HTML on the fly from any RSS feed. 

I was using this code on the footer our company website. You are welcome to look at there for an example.
www.internetbuilderconsulting.com

Also, fyi, Feed Informer does not offer their own code for what I am doing and they do not offer ASP (vbScript) code. However, we (a friend Carol) worked with me to write the ASP code above to import the outputed HTML from Feed Informer. I wrote everything else. 

Once you know your Widget ID, and you have set up the Widget Template, all you need is the Widget ID from Feed Informer to make the ASP code work. You do not need to use ANY their code, the code I am providing below is all you will need.

The rest of the code is in this project including the JS, JQuery and CSS. Hopefully you can follow it fairly easy. 

I do appolgize, I normally I put better comments in my help files. I was just throwing it up on my GitHub so I could archive it for sharing with others (I am just now starting to do that more).

Enjoy.

###Final Comments

If I was to change something, I would not use OnClick. It is bad SEO because Google does not follow onClick events, only HREF links. I will probably fix it. It would have worked better using a standard HREF with a target="_blank" link. I wrote this code a while back and I am not sure why I did it that way. I will make changes to it later if I have time.



