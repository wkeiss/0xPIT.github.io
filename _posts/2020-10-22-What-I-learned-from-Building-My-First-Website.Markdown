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

Recently I am learning Web Development by doing  HTML, CSS, and Javascript challenges. One of the CSS challenges is to find an open-source web design and achieve it without copying resource codes. I worked with websites every day not as a developer but as customer support in a Sass company.  I was quite curious about how a website is made.  so I decided to build a site styling as I saw at my work.

Before doing the task, my challenges about HTML and CSS are easy to achieve, they are all static blog pages, like the one shown below. I was quite happy when I achieved HTML and CSS code on my own. And I was thinking" Hmm, Building a website is not very hard". But after I started trying to achieve the website I chose,  I soon realized how much native I was. It not very hard to make a website, but if you want to have a good user interface interactive experience and beautiful interface, you need to devote yourself to every possible detail, like choose the proper color and the font style, the hover effect, and make the resource load fastly when the user opens the site and etc. If you take full advantage of the Searching Engine and be open to new things, you will find a way to achieve them, so it's not hard. But overall, it's complicated.

![a simple static blog page](../assets/images/blog-image/simple-static-blog-page.jpg)

## Choose an open source design

I chose [a theme](https://demo.themewagon.com/preview/timer-free-responsive-multi-page-personal-bootstrap-template) in the site [Free Open Source Bootstrap HTML5 CSS3 Website Templates @ ThemeWagon](https://themewagon.com/theme_tag/open-source/) and downloaded the source code so I can have the pictures used in the website.  I know the author use bootstrap to build the site, but my focus on building a website use CSS, HTML, and Javascript only, don't use the framework.

## Write HTML

I wrote the HTML of the home page through the live site. I thought I won't have problems with writing HTML,  but I met a challenge soon. I couldn't achieve the icons with HTML I learned. I don't know which tag I should use,  I should use <div>and insert the icon picture or there is something I don't know to achieve the icon. So I decided to Google. 

![The section with icons I don't know how to achieve](../assets/images/blog-image/icon-section.jpg)

Before I googled, I looked at the source code, I found there were no icon pictures shown above, and the related code I couldn't understand. I just wanted to achieve the design using what I learned rather than copy the source code before, so I won't try to understand the source of how to build these icons. I searched online I couldn't found the same icons, so I decided not to achieve this section. But there were social icons in the footer I need to achieve. Then I googled, there is an article in W3School about the topic: [How To Create Social Media Buttons](https://www.w3schools.com/howto/howto_css_social_media_buttons.asp). So I followed the instructions：

1.  Add the icon library, put the link in my HTML Header Tags

   `<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">`

2. Add social icon font

   `<a href="#" class="fa fa-facebook"></a>`

   ` <a href="#" class="fa fa-twitter"></a>`

   `<a href="#" class="fa fa-linkedin"></a>
   <a href="#" class="fa fa-google"></a>`

   

3. You can style the social icons like style fonts, like add color or font-size to them.

And also there is another challenge in HTML is how to achieve the dropdown menu icons. I wanted to only achieve one page only for the first time, so I skipped the dropdown menu also. From now on, I have ended my HTML coding.

## Write CSS

Now it's time to add CSS to style my site. From the beginning, I would like to set the style to the body:

`body{
	margin: 0;
	width: 100vW;
}`

Later I get used to adding the background color or background images firstly. Then I will focus on the layout of different sections. The header is the first section I need to figure it out. I found if I need to make the logo and the navigation sit at the start and end of the header, I need to use CSS code float: right; to let the navigation float to the right of its father element, but it was weird. It isn't what I’d like to, so I only can change to the grid layout. Why do I use a grid layout rather than flex? Since I know grid layout but I don't know flex. I met the same things when I tried to use `float` peoperty to have 2 items on the left and right layout. And I use the gird layout to change the layout too. Even I can achieve the design, but I was lack of CSS layout knowledge. After I finished the CSS challenge, I decided to learn the CSS layout knowledge on MDN. I found in different sections, it's better to use `<div>` to wrap the content, so you can more easy to apply CSS to the whole content to create a better out looking. 

Later, there was a gird section to show works, after I wrote the gird CSS to the section, it didn't work. I checked the grammar again and again, and sure I have set the right gird CSS code. But no matter how I refreshed the HTML, the grid layout didn't be applied. So I put my code to Stackoverflow to ask for help, 1 minute later after I post the question, I got an answer. It's amazingly fast! And he said I had a typo in `lastestwork`. After I changed the spelling, the grid layout applied, thanks for pointing it out! From this experience, I know I should carefully check the spelling firstly when I met an error.

But after the grid layout applied, all the images gird items are all overflow, what a terrible. I changed the width of grid columns, but the images were still what they are, it seems that the images are out of control of the grid layout. I searched ask for solutions again, and the solution I found was to put the image to the div tag, so the div should be the grid item, and grid layout can take effect on it. Yes, my code showed it's true. But images still will overflow the div section wrapping it, so you need to add `max-width:100 %`; `max-height:100% `to make the images smaller to adjust the div section wrapping it.

After these troubles, and change the color to some content, change the font style. My site looks not bad on my laptop screen, it looks like 98% same to the design. But if change the screen to smaller, the layout becomes messy. Oh my god~It's like you thought you have arrived at the end, but someone tells you there are still 100 miles to be there! I had never known there was so much work behind a simple page.

I found the design I am going to achieve has a smaller screen version, like phone and iPad versions. The layout in the Ipad version same as on PC, but it's different in the phone version. The navigation change to a Hamburger icon, and if we click the icon, the navigation menu will show. And the gird section will change the layout to only show one item in a line. How to make the layout change after the screen change to a smaller width?

I was trying to make up my knowledge of layout on MDN, in there, I know `@media query`， which can help you set the CSS for the different screen width. The format is:

`@media only screen and (max-width: ..){ `

​			`	/* add your css code here */`

`}`

 If the width of the screen equal to or smaller than the max-width you set, then the CSS code will be applied. If I want to change the grid section layout to show an item in a line, I need to change the section's display to block value. It's simple, but the @media style on the header a little bit complex. The navigation menu is shown by default. And if I want to change to a hamburger icon, and later I need it can show after I click the icon, what should I do? First, my thought is to make the navigation hidden, so the icon can replace the navigation. And I should add the Javascript to make the navigation show after I clicked the icon. But the Javascript code I added didn't make the changes. So I what I did was googled for a solution :)

And Luckily again, I got the solution. The solution is to add the icon to HTML, use CSS to hide the navigation, and use Javascript to change the navigation class name, and use the new class name as a selector to change the style of navigation. It turns out it works on my site. 

Well, after writing down my first site-building experience, I think nobody will spend time to read these long words. I wonder can I write it better to make the article more attractive to make readers like to read it more. The motivation for writing this post is to use words to remember the experience of learning Web Development. I hope I can review my pathway of learning web development through the words I wrote today. If people would like to read my articles more likely because through this article, they know how to fix the issues I meet, like how to make the navigation menu show or hidden in the phone version. I was not going to make a tutorial, since these issues I wrote can get the solutions via Google, they are so common that I can find the answer easily. People can find the answers online easily either, so I don't need to spend extra time writing the solution again.

