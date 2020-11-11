---
title: "What I Learned from Building My First Site"
layout: post
date: 2020-10-18
tag:
- "2020"
- "blog"
- "growth"
- ”work"
blog: true

---

Recently I am learning Web Developmet by doing  HTML, CSS and Javascript chanllenges. One of the CSS challenge is  to find an open source web design and achieve it without copying resource codes. I worked with websites every day not as a developer but as a cutomer support in a Sass company.  I was quite curious about how a website be made.  so I decided to build a site styling like I seen at my work.

Before doing the task, my challenges about HTML and CSS are easy to achieve, they are all static blog pages, like the one show below. I was quite happy when I achieved with my HTML and CSS code by my own. And I was thinking" Hmm, Building a website is not very hard". But after I started trying to achieve the website I chose,  I soon realized how much native I was. It not very hard to make a website, but if you want to have good user interface interavcitve experience and beatiful interface, you need to devote yourself to every possible details, like choose the proper color and the font style, the hover effect, and make the resource load fastly when the user open the site and etc. If you take full advantage of the Searching Engine, and be open for new things, you will find the way to achieve them, so it's not hard. But overall, it's complicated.

![a simple static blog page](../assets/images/blog-image/simple-static-blog-page.jpg)

## Choose an open source design

I chose [a theme](https://demo.themewagon.com/preview/timer-free-responsive-multi-page-personal-bootstrap-template) in the site [Free Open Source Bootstrap HTML5 CSS3 Website Templates @ ThemeWagon](https://themewagon.com/theme_tag/open-source/) , and downloaded the source code so I can have the pictures used in the website.  I know the author use bootstrap to build the site, but my focus on building a website use CSS, HTML, and Javascript only, don't use framework.

## Write HTML

I wrote the HTML of the home page through the live site. I thought I won't have problems in writing HTML,  but I met a challenge soon. I couldn't achieve the icons with HTML I learnt. I don't know which tag I should use,  I should use <div>and insert the icon picturce or there is something I don't know to achieve the icon. So I decided to Google. 

![The section with icons I don't know how to achieve](../assets/images/blog-image/icon-section.jpg)

Before I googled, I looked at the source code, I found there was no the icon pictures shown above, and the related code I couldn't understand. I just wanted to achieve the design using what I learnt rather than copy the source code before, so I won't try to understand the source how to build these icons. I searched online I coudn't found the same icons, so I decided not do achieve this section. But there were social icons in the footer I need to achieve. Then I googled, there is an article in W3School about the topic: [How To Create Social Media Buttons](https://www.w3schools.com/howto/howto_css_social_media_buttons.asp). So I followed the instructions：

1.  Add the icon libarary, put the link in my HTML Header tags

   `<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">`

2. Add social icon font

   `<a href="#" class="fa fa-facebook"></a>`

   ` <a href="#" class="fa fa-twitter"></a>`

   `<a href="#" class="fa fa-linkedin"></a>
   <a href="#" class="fa fa-google"></a>`

   

3. You can style the social icons like style fonts, like add color or font-size to them.

And also there is another challenge in HTML is how to achieve the dropdown menu icons. I wanted to only achieve one page only in the first time, so I skiped the dropdown menu also. From now, I have end my HTML coding.

## Write CSS

Now it's time to add css to style my site. From the beginning, I would like to set style to the body:

`body{
	margin: 0;
	width: 100vW;
}`

Later I get used to add the background color or background images firstly. Then I will focus on the layout of diffrent sections.  header is the first section I need to figure it out. I found if I need to make the logo and the navigation sit at the start and end of header, I need to use css code `float:right;` to let the navagation float to the right of its father element, but it was weird. It isn't not what I’d like to, so I only can change to grid layout. Why do I use grid layout rather than flex? Since I know grid layout but I don't know flex. I met the same things when I tried to use flad to have 2 items in left and right layout. And I use the gird layout to change the layout too. Even I can achieve the design, but I was lack of CSS layout knowlegdes. After I finished the css challenge, I decided to learn the CSS layout knowledge on MDN. I found in diffrent sections, it's better to use `<div>` to wrap the content, so you can more easy to apply CSS to the whole content to create better outlooking. 

Later, there was a gird section to show works, after I wrote the gird css to the section, it didn't work. I checked the grammer again and again, and denifitely sure I have set right gird css code. But no matter how I refreshed the HTML, the grid layout didn't applied. So I put my code to Stackoverflow to ask for help, 1 minute later after I post the question, I got an answer. It's amazing fast! And he said, I have a typo in "lastestwork". After I changed the spelling, the grid layout applied, thanks for pointing it out! From this experience, I know I should carefully check the spelling fistly when I met an error.

But after the grid layout applied, all the images gird items are all overflow, what a terriable.  I changed the width of grid columns, but the images were still what they are, it seems that the images are out of control of the gird layout. I searched ask for solutions again, and solution I found was put the image to `div` tag, so the `div` should be the grid item, and grid layout can take effect on it. Yes, my code shown it's true. But img still will overflow the `div` section wrapping it, so you need to add `max-width:100 %;` `max-height:100%` to make the images become smaller to adjust the div section wrapping it.

After these troubles, and change the color to some content, change the font style. My site looks not bad on my laptop screen, it looks like 98% same to the desigin. But if change the screen to smaller, the layout become messy. Oh my god~It's like you thought you have arrive at the end, but someone tell you there are still 100 miles to be there! I had never knew there were so much work behind a simple page.

I found the design I am going to achieve has smaller screen version, like phone and iPad versions. The layout  in Ipad version same as on PC, but it's differnt in phone version.  The navigation change to a Hamburger icon , and if we click the icon, the navigaiton menu will show.  And the gird section will change the layout to only show one items in a line. How to make the layout change after the sreen change to smaller width?

I was try to make up my knowledge of layout on MDN, in there, I know `@media query`， which can help you set the css for different screen width. The format it is:

`@media only screen and (max-width: ..){ `

​			`	/* add your css code here */`

`}`

 If the width of screen equal to or smaller than the max-width you set, then the css code will be applied. If I want to change the grid section layout to show a items in a line, I need to change to the section's dispaly to block value.  It's simple, but the @media style on header  a little bit complex. The navigaiton menu is shown by defualt. And if I want to change to a hamburger icon, and later I need it can show after I click the icon, what should I do? First my thought is make the navigation hidden,  so the icon can replace the navigation. And  I should add the Javascript to make the navigation show after I clicked the icon. But the Javascript code I added didn't make the changes. So I what I did was seached online ask for a soulution :)

And Luckily again, I got the solution. The solution is add the icon to HTML,  use CSS to hidde the navigation,  and use Javascript to change the navigation class name, and use the new class name as selector to change the style of navigaiton. It turns out it works on my site. 

Well, after writing this long articles to record the first site building,  I think nobody will spend time to read these words. I wonder can I write it better to make the article more attractive to make readers like to read it more. The motivation of writing this post is to use words remember the experience of learning Web Development. I hope I can review my pathway of become a web developer through the words I wrote today.  If people would like to read my articles more likely because through this article, they know how to fix the issues I meet,  like how to make the navigation menu show or hidden in phone version. I was not going to make a turiol, since these issues I wrote can get the solutions via Google,  they are so common that I can find the answer easily. People can find the answers online easily either, so I don't need to spend extra time to wrote the solution again.

