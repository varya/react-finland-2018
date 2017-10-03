---

layout: sc5

style: |

    #custom {
      background: black;
      padding-top: 0;
    }
    #custom h2 {
      color: yellow;
      margin-top: 70px;
    }

    .no-title h2 {
      display: none;
    }
---

# Component development with CSS in 2017 {#cover}

Varya Stepanova, <span class="position">Senior Software Specialist at SC5 Online</span>
{:.author}


## Me
{: .no-title }

### Now
Senior Software Specialist at SC5 Online

### Before
TMG (Amsterdam, the Netherlands); Yandex&nbsp;(Moscow,&nbsp;Russia)

### Area of expertise
Components on the web: design systems, pattern libraries, SGDD, BEM. Techs: CSS, JavaScript, etc.

<!--
Before we start, I would like to introduce myself and explain why
this topic has been chosen.
-->


## Spoiler

* Industry challenges when developing CSS
* Today's solutions for components on the web
* Web Components and the future of CSS
* Style Guide Driven Development

<!--
This is what I'm going to show today
  https://www.styled-components.com/
  https://vuejs.org/v2/guide/single-file-components.html#For-Users-New-to-Module-Build-Systems-in-JavaScript
  CSS modules
  CSS-in-JS

  https://speakerdeck.com/okonet/modular-css-v2-css-in-js-edition
-->


## CSS

> *Cascading Style Sheets* (CSS) is a style sheet language used for describing the look and formatting of a document
> written in a markup language. <cite>[Wikipedia](https://en.wikipedia.org/wiki/Cascading_Style_Sheets)</cite>

First published in 1996
{: .note}

<!--
The meaty part of the lecture is about CSS.
Are you familiar with this technology?

CSS is used to style web documents. CSS rules can be matched to DOM nodes and bring them view which
is descriped with CSS properties.

This concept is pretty old. CSS was first introduced in 1996. And nothing conceptually has been changed since then.
However the web now is far more complex than in 1996, so in industry we are facing the chalelngies and need a way to
overcome.
-->


## Industry challenges
{: .no-title }

![](pictures/homepage.png)

<!--
In this picture you can see how the web pages used to look like. And from the architectural point of view they were
similar. The industry just did not have experience back then to provide recommendations how to build the we good.

Now things have already changed. Today, if you are developing not you cat's homepage but a serious website, it should
meet the requirements.
-->


## Bulletproof Web Desing
{: .bulletproof .no-title }

<!--
This problem was first spoken out loud by this gentelman. His name is Dan Cederholm and he is the author of the book
shown. The "Bulletproof Web Design" is a first place where the inductry needs were explained.
In was first published in 2005 and has 2 more editions since then. However this is quite mature book, I still recommend
it if you want to step in the industry level of creating web sites.
He first said that the HTML/CSS markup we produce should be stable. It should be maitainable meaning not very sensetive
to the providing changes.
So, it's not like single action - provide the code and forget about it. A developer will get back to their code to fix
something. Other developers will bring their changes into the code. And nothing should be broken in unexpected places.
-->

<style>
.bulletproof {
  background-image:
    url('pictures/bulletproof.jpg'),
    url('pictures/dan-cederholm.jpg');
  background-position: top right, -120px 0;
  background-size: auto, 100%;
  background-repeat: no-repeat;
}
</style>


## Big CSS

* massive sites
* big teams of developers
* heavy UI
* long running projects

<!--
massive sites: A lot of code, thousands of lines
big teams of developers: up to hundreds of ppl, teams can grow and change
heavy UI: each piece of interface has a lot of code and logic behind
long running project: need to be maintainable
-->


## Massive web sites

* Thousands of lines of code
* A lot of files
* Many pages
{: }

* A lot of websites with common codebase
* Common corporate style

<!--
You cannot check all the pages visially for every change, so your code should be written the way which
makes it possible to predict.

A lot of websites with common codebase: repeating would be too expensive.
-->


## Big teams

* Hundreds of developers
* Growing teams
* Changing the context

<!--
Hundreds of people.
Developers need common approaches.
Communication matters.
-->


## Heavy UI
{: .heavy-ui .no-title }

<!--
This login form in the middle does not look as a massive component.
Just 2 inputs, checkbox, button.
Guess how much code is needed to represent it?
-->

<style>
.heavy-ui:before {
  display: block;
  content: '';
  background-image: url(pictures/domik.png);
  background-size: contain;
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
}
</style>


## Heavy UI
{: .heavy-ui-code .no-title }

    <form class="b-mail-domik g-js" method="post" action="https://passport.yandex.com/passport?mode=auth&amp;from=mail&amp;origin=hostroot_com_nol_enter&amp;retpath=https%3A%2F%2Fmail.yandex.com">
      <i class="b-mail-domik__roof"></i>
      <table class="b-mail-domik__shadow">
        <tbody>
          <tr>
            <td class="b-mail-domik__shadow__lt">&nbsp;</td>
            <td class="b-mail-domik__shadow__t"></td>
            <td class="b-mail-domik__shadow__rt">&nbsp;</td>
          </tr>
          <tr>
            <td class="b-mail-domik__shadow__l">&nbsp;</td>
            <td class="b-mail-domik__shadow__m">
              <div class="b-mail-domik__form">
                <div class="b-mail-domik__username">
                  <label class="b-hint-input g-js" for="b-mail-domik-username11" style="display: block;">username</label>
                  <div class="b-input"><input tabindex="1" name="login" id="b-mail-domik-username11" class="b-input__text" autocapitalize="off" autocorrect="off" aria-label="username"></div>
                </div>
                <div class="b-mail-domik__password">
                  <label class="b-hint-input g-js" for="b-mail-domik-password11">password</label>
                  <div class="b-input"><input type="password" tabindex="2" name="passwd" id="b-mail-domik-password11" class="b-input__text" aria-label="password"></div>
                </div>
                <div class="b-mail-domik__permanent"><input type="hidden" name="twoweeks" value="yes"><input type="checkbox" tabindex="3" id="b-mail-domik-permament11" class="b-mail-domik__check">&nbsp;<label for="b-mail-domik-permament11">don't remember me</label></div>
                <div class="b-mail-domik__button b-mail-domik__button_qr"><span class="b-mail-button b-mail-button_default b-mail-button_button b-mail-button_grey-26px b-mail-button_26px b-mail-button_lead"><span class="b-mail-button__inner"><span class="b-mail-button__text">Log in</span></span><input type="submit" tabindex="4" class="b-mail-button__button" value="Log in"></span><a href="https://passport.yandex.com/auth/?mode=qr&amp;retpath=https%3A%2F%2Fmail.yandex.com" class="js-button-qr b-mail-button b-mail-button_default b-mail-button_button b-mail-button_grey-26px b-mail-button_26px b-mail-button_dependent"><span class="b-mail-button__inner"><span class="b-mail-button__ico b-mail-button__ico_qr"></span></span></a></div>
                <div class="b-mail-domik__remember"><a tabindex="5" class="b-mail-domik__remind js-count-click" href="https://passport.yandex.com/passport?mode=restore" data-metrika="Клики на 'Вспомнить пароль'" data-paranja="check">Forgot your password?</a></div>
                <div class="b-mail-domik__social"><a class="b-mail-domik__social-link js-social-link" data-provider="fb"><i class="b-mail-domik__social-icon b-mail-domik__social-icon_provider_fb"></i></a><a class="b-mail-domik__social-link js-social-link" data-provider="tw"><i class="b-mail-domik__social-icon b-mail-domik__social-icon_provider_tw"></i></a><a class="b-mail-domik__social-link js-social-link" data-provider="gg"><i class="b-mail-domik__social-icon b-mail-domik__social-icon_provider_gg"></i></a></div>
              </div>
            </td>
            <td class="b-mail-domik__shadow__r">&nbsp;</td>
          </tr>
          <tr>
            <td class="b-mail-domik__shadow__lb">&nbsp;</td>
            <td class="b-mail-domik__shadow__b"></td>
            <td class="b-mail-domik__shadow__rb">&nbsp;</td>
          </tr>
        </tbody>
      </table>
      <div class="antivirus js-antivirus">Yandex.Mail has <a href="http://www.drweb.com/" target="_blank"></a> virus protection</div>
    </form>

<!--
So, this is HTML.
And almost every node here needs CSS. Not one property but many.
-->

<style>
.heavy-ui-code pre code {
  font-size: 7px;
}
</style>


## Long running projects

* Code lives for years
* Continious development

<!--
In the web development you cannot create version 2, we provide changes little by little
So, the code should be maintainable for years
-->


## Where CSS is hard?
{: .slide--shout .slide--red }


## Is this good?

    H1 { color: blue }
    P EM { font-weight: bold }
    A:link IMG { border: 2px solid blue }
    A:visited IMG { border: 2px solid red }
    A:active IMG { border: 2px solid lime }

<!--
Now look at this code. Do you see something strange? Any guess?
Who would write their CSS like this?

The problem is that CSS was created to make text bold and links underlined. It ideally suited
solving these problems. In many websites developers still use CSS like.

Actually this code from [CSS level 1 specification](http://www.w3.org/TR/CSS1/). It is
very simple, was recommended in 1996. Time passed and we met new chalenges.
-->


## What makes CSS hard?

* Vertical centering
* Equal height columns
* Browser inconsistencies
* Unobvious tricks
{: .next }

<!--
Before we decide what is wrong with that peice, let's guess what is hard in CSS.

When ppl are asked, the repson is usually
- vertical centing
- making columns of equial height
- browers render CSS differently, so it takes special knowledge and work to make the interface consistent
- many solutions are unobvious tricks which needed to be memorized

But this is not true, this is easy or at least clear how to manage. You can google for all this questions.
-->


## What <b>really</b> makes CSS hard?

* Scoping
* Specificity conflicts
* Non-deterministic matches
* Dependency management
* Removing unused code

<!--
The real hard problems of CSS are here:
- No scoping. Everything is CSS is global.
- Specificity conflicts. I'll explain in detal later.
- Non-deterministic matches which naturally result from declarativeness of CSS language
- Dependency management
- Removing unused code
-->


## CSS has no scoping

    a { /* Affects all the links */
      color: red;
    }
    ul li a { /* Affects all the links in lists */
      color: green;
    }

<!--
This especially maters if you link third-party CSS.
A common problem for developing libraries or code which will be later delivered to another web site.
Everything in CSS is global, and writing good CSS is similar to writing a good program module if you only allowed to use
global variables.
This can be mixed with another CSS and applied to wrong nodes.
Writing good CSS means you has to predict the future.
-->


## Specificity

> Specificity is the means by which a browser decides which property values are the most relevant to an element and gets
> to be applied. Specificity is only based on the matching rules which are composed of selectors of different sorts.

<!--
Another problem is specificity.
Who remember what specificity is?
Ok, I will explain.
-->


## The most specific matters

    <div id="test">
      <span>Text</span>
    </div>

<separator/>

    div#test span { color: green }
    span { color: red }
    div span { color: blue }

<!--
If a brower has 2, 3 or more rules which match the same DOM node, how it decides what are the properties to take into
work?
The order does not matter.
For every selector a browser calculates how important this set of rules is. The rule with the more specific selector
would be prioritized.
So, here we see...
-->


## How to overwrite?

    <div class="sidebar">Left floated sidebar</div>

<separator/>

    .sidebar { /* Does it redefine `div.sidebar`?! */
      float: right;
    }
{: .next }

<separator/>

    body .sidebar { /* Overwrites 'div.sidebar {}' */
      float: right;
    }
{: .next }

<!--
When it comes to developments, specificity matters when redefining pre-given
components.

To redefine the left-floated sidebar, we would overwrite the rule.
-->


## Specificity hell
{: .no-title }

    .navbar-inverse .navbar-nav>li>a {
      color: #999;
    }

    #home-menu-container #home-menu li a {
      color: red;
    }

    body #home-menu ul li a {
      color: blue !important;
    }

<!--
People ask on Stackoverflow how to overwrite Bootsrtap
These things can be in different files
-->


## Non-deterministic matches

    #content div div {
      float: left;
    }

<!-- This can be matched to anything -->
<!-- You cannot rely on the document structure, because it contantly changes while developing -->
<!-- в момент, когда ты пишешь, ты указываешь признаки нод, на которые сматчится правило, а не точный адрес. смотри:
можно писать адрес «Rettigweg 1, 13187 Berlin", а можно «около Wollankstrasse такая боковая улица с тремя домами, и
там есть такой желтый дом, и там на втором этаже ещё балконы металлические с узорами» -->


## Dependency management
{: .dependency-management }

### No dependencies, sorry

<div class="next" markdown="1">
### But what about?

    @import url('i-need-this.css');
</div>

### No, sorry again.
{: .next .sorry }

<!--
CSS was not developed as a programming language and now it still isn't. So, there is no way to declare that
one piece of CSS needs anotehr one.
OK, there is import. But this is not  aproduction solution. And assuming undeterministic matches we cannot rely on it.
-->

<style>
.dependency-management h3 {
  padding-top: 1em;
  margin-bottom: 0.5em;
}
.dependency-management .sorry
{
  color: green;
}
</style>


## Removing unused code

100 pages in projects

    .person div a {
      color: pink;
    }

Can I remove it? Will it break something? Maybe it is for a third-party HTML code?

<!--
CSS is declarative, so you cannot say what are the nodes the rules will aply to.
If you have a lot of pages you cannot remove a piece of CSS and check visually if something is broken.
Even worse with  dynamic web sites.
-->


## Where CSS is hard?
{: .no-title .hard-css }

<table><thead>

<th markdown="1">

This is not hard in CSS

</th>

<th markdown="1">

This is!

</th>

</thead><tr>

<td markdown="1">

    #sidebar ul li a {
      <mark>color: red;</mark>
      <mark>display: block;</mark>
      <mark>padding: 1em;</mark>
    }

</td>

<td markdown="1">

    <mark>#sidebar ul li a</mark> {
      color: red;
      display: block;
      padding: 1em;
    }

</td>

</tr></table>

*How do we architect encapsulated components?*
{: .next }

<!--
Writing CSS is easy. It is very easy to read and it is very likely that you can
find the tricks you need at Stackoverflow. But architechting CSS is very difficult.

We need a way to architect independent encapsulated components.
Being put into any place on the page, the components should not break anything. Also, it should not be broken
itself.
-->

<style>
.hard-css em {
  font-size: 30px;
}
</style>


## Where am i?

The following slides demonstrate presentation **written in markdown** and *shown in html*, directly from the GitHub.

Based on these technologies

* [Shower, presentation engine](https://github.com/shower/shower)
* [Jekyller, md->html generator](https://github.com/shower/jekyller)
* [SC5 brand styles for Shower](https://sc5.github.io/shower-sc5/)


## Kinds of slides
{: .slide--shout .slide--red }


## Blank slide


## Plain text

Design strategy is a management tool to deliver world class user interfaces and enable excellent user experience. In the
future, UX aspects will become naturally considered as a part of product strategy. Before this happens, it seems
necessary to manage UX strategy specifically. This post reveals the secret weapon SC5 uses in designing strategy.

Spoiler: no weapon, we are just awesome.
{: .note }


## Inline elements

Essential part of the [design leadership]() practice are the tools and methods deployed by the leaders. The details of
**strategy, vision and roadmap** documents all depend on the domain of business. Style and brand guides intersect design
with marketing. In business-to-consumer business, interesting challenge is the increasing number of channels or
touchpoints in which customers *engage with the company*. Without a coherent approach under design leadership, everything
can <code>fall apart</code>.


## we can — we share — we care
{: .slide--shout .slide--red }


## we can — we share — we care
{: .slide--shout .slide--azure }
<img src="themes/sc5/images/icons/heart.svg" class="svg" style="width: 200px; height: 200px;"/>


## full image
{: .slide--full-image }

![](images/SC5-mikael-ja-matti.jpg)


## Brand icons
{: .slide--shout .slide--azure }


## Icons cheatsheet
{: .icon-cheatsheet }

<img src="themes/sc5/images/icons/monkey--meh.svg" class="svg" />
<img src="themes/sc5/images/icons/star.svg" class="svg" />
<img src="themes/sc5/images/icons/bulb.svg" class="svg" />
<img src="themes/sc5/images/icons/monkey--smile.svg" class="svg" />
<img src="themes/sc5/images/icons/graph.svg" class="svg" />
<img src="themes/sc5/images/icons/clock.svg" class="svg" />
<img src="themes/sc5/images/icons/brilliant.svg" class="svg" />
<img src="themes/sc5/images/icons/strings.svg" class="svg" />
<img src="themes/sc5/images/icons/loop.svg" class="svg" />
<img src="themes/sc5/images/icons/graph.svg" class="svg" />
<img src="themes/sc5/images/icons/monkey--happy.svg" class="svg" />
<img src="themes/sc5/images/icons/key.svg" class="svg" />
<img src="themes/sc5/images/icons/rocket.svg" class="svg" />
<img src="themes/sc5/images/icons/puzzle.svg" class="svg" />
<img src="themes/sc5/images/icons/duck.svg" class="svg" />
<img src="themes/sc5/images/icons/circles.svg" class="svg" />
<img src="themes/sc5/images/icons/tag.svg" class="svg" />
<img src="themes/sc5/images/icons/anchor.svg" class="svg" />
<img src="themes/sc5/images/icons/heart.svg" class="svg" />
<img src="themes/sc5/images/icons/mark.svg" class="svg" />
<img src="themes/sc5/images/icons/grow.svg" class="svg" />
<img src="themes/sc5/images/icons/toolbox.svg" class="svg" />
<img src="themes/sc5/images/icons/dog.svg" class="svg" />
<img src="themes/sc5/images/icons/rocket--launch.svg" class="svg" />
<img src="themes/sc5/images/icons/arrow.svg" class="svg" />
<img src="themes/sc5/images/icons/lambda.svg" class="svg" />
<img src="themes/sc5/images/icons/compas.svg" class="svg" />
<img src="themes/sc5/images/icons/propeller.svg" class="svg" />
<img src="themes/sc5/images/icons/puzzle--turned.svg" class="svg" />
<img src="themes/sc5/images/icons/wheel.svg" class="svg" />
<img src="themes/sc5/images/icons/robot.svg" class="svg" />
<img src="themes/sc5/images/icons/pile.svg" class="svg" />
<img src="themes/sc5/images/icons/vinyl.svg" class="svg" />
<img src="themes/sc5/images/icons/lens.svg" class="svg" />
<img src="themes/sc5/images/icons/lips.svg" class="svg" />
<img src="themes/sc5/images/icons/cloud.svg" class="svg" />
<img src="themes/sc5/images/icons/cellphone.svg" class="svg" />
<img src="themes/sc5/images/icons/pipo.svg" class="svg" />
<img src="themes/sc5/images/icons/boat.svg" class="svg" />
<img src="themes/sc5/images/icons/worker.svg" class="svg" />
<img src="themes/sc5/images/icons/engineer.svg" class="svg" />
<img src="themes/sc5/images/icons/wrench.svg" class="svg" />
<img src="themes/sc5/images/icons/spycam.svg" class="svg" />
<img src="themes/sc5/images/icons/pi.svg" class="svg" />
<img src="themes/sc5/images/icons/molecule.svg" class="svg" />
<img src="themes/sc5/images/icons/lamp.svg" class="svg" />
<img src="themes/sc5/images/icons/cup.svg" class="svg" />
<img src="themes/sc5/images/icons/mill.svg" class="svg" />
<img src="themes/sc5/images/icons/vial.svg" class="svg" />
<img src="themes/sc5/images/icons/termo.svg" class="svg" />
<img src="themes/sc5/images/icons/excavator.svg" class="svg" />
<img src="themes/sc5/images/icons/first-aid.svg" class="svg" />
<img src="themes/sc5/images/icons/ketler.svg" class="svg" />
<img src="themes/sc5/images/icons/teapot.svg" class="svg" />
<img src="themes/sc5/images/icons/molecule--turned.svg" class="svg" />
<img src="themes/sc5/images/icons/wrench--ring.svg" class="svg" />
<img src="themes/sc5/images/icons/monkey--unhappy.svg" class="svg" />
<img src="themes/sc5/images/icons/bulb--light.svg" class="svg" />
<img src="themes/sc5/images/icons/star-treck.svg" class="svg" />

<style>
  .icon-cheatsheet .svg {
    margin: 10px;
  }
</style>


## Icons cheatsheet
{: .icon-cheatsheet .slide--red }

![](themes/sc5/images/icons/monkey--meh.svg){: .svg }
![](themes/sc5/images/icons/star.svg){: .svg }
![](themes/sc5/images/icons/bulb.svg){: .svg }
![](themes/sc5/images/icons/monkey--smile.svg){: .svg }
![](themes/sc5/images/icons/graph.svg){: .svg }
![](themes/sc5/images/icons/clock.svg){: .svg }
![](themes/sc5/images/icons/brilliant.svg){: .svg }
![](themes/sc5/images/icons/strings.svg){: .svg }
![](themes/sc5/images/icons/loop.svg){: .svg }
![](themes/sc5/images/icons/graph.svg){: .svg }
![](themes/sc5/images/icons/monkey--happy.svg){: .svg }
![](themes/sc5/images/icons/key.svg){: .svg }
![](themes/sc5/images/icons/rocket.svg){: .svg }
![](themes/sc5/images/icons/puzzle.svg){: .svg }
![](themes/sc5/images/icons/duck.svg){: .svg }
![](themes/sc5/images/icons/circles.svg){: .svg }
![](themes/sc5/images/icons/tag.svg){: .svg }
![](themes/sc5/images/icons/anchor.svg){: .svg }
![](themes/sc5/images/icons/heart.svg){: .svg }
![](themes/sc5/images/icons/mark.svg){: .svg }
![](themes/sc5/images/icons/grow.svg){: .svg }
![](themes/sc5/images/icons/toolbox.svg){: .svg }
![](themes/sc5/images/icons/dog.svg){: .svg }
![](themes/sc5/images/icons/rocket--launch.svg){: .svg }
![](themes/sc5/images/icons/arrow.svg){: .svg }
![](themes/sc5/images/icons/lambda.svg){: .svg }
![](themes/sc5/images/icons/compas.svg){: .svg }
![](themes/sc5/images/icons/propeller.svg){: .svg }
![](themes/sc5/images/icons/puzzle--turned.svg){: .svg }
![](themes/sc5/images/icons/wheel.svg){: .svg }
![](themes/sc5/images/icons/robot.svg){: .svg }
![](themes/sc5/images/icons/pile.svg){: .svg }
![](themes/sc5/images/icons/vinyl.svg){: .svg }
![](themes/sc5/images/icons/lens.svg){: .svg }
![](themes/sc5/images/icons/lips.svg){: .svg }
![](themes/sc5/images/icons/cloud.svg){: .svg }
![](themes/sc5/images/icons/cellphone.svg){: .svg }
![](themes/sc5/images/icons/pipo.svg){: .svg }
![](themes/sc5/images/icons/boat.svg){: .svg }
![](themes/sc5/images/icons/worker.svg){: .svg }
![](themes/sc5/images/icons/engineer.svg){: .svg }
![](themes/sc5/images/icons/wrench.svg){: .svg }
![](themes/sc5/images/icons/spycam.svg){: .svg }
![](themes/sc5/images/icons/pi.svg){: .svg }
![](themes/sc5/images/icons/molecule.svg){: .svg }
![](themes/sc5/images/icons/lamp.svg){: .svg }
![](themes/sc5/images/icons/cup.svg){: .svg }
![](themes/sc5/images/icons/mill.svg){: .svg }
![](themes/sc5/images/icons/vial.svg){: .svg }
![](themes/sc5/images/icons/termo.svg){: .svg }
![](themes/sc5/images/icons/excavator.svg){: .svg }
![](themes/sc5/images/icons/first-aid.svg){: .svg }
![](themes/sc5/images/icons/ketler.svg){: .svg }
![](themes/sc5/images/icons/teapot.svg){: .svg }
![](themes/sc5/images/icons/molecule--turned.svg){: .svg }
![](themes/sc5/images/icons/wrench--ring.svg){: .svg }
![](themes/sc5/images/icons/monkey--unhappy.svg){: .svg }
![](themes/sc5/images/icons/bulb--light.svg){: .svg }
![](themes/sc5/images/icons/star-treck.svg){: .svg }


## Icons cheatsheet
{: .icon-cheatsheet .slide--azure }

![](themes/sc5/images/icons/monkey--meh.svg){: .svg }
![](themes/sc5/images/icons/star.svg){: .svg }
![](themes/sc5/images/icons/bulb.svg){: .svg }
![](themes/sc5/images/icons/monkey--smile.svg){: .svg }
![](themes/sc5/images/icons/graph.svg){: .svg }
![](themes/sc5/images/icons/clock.svg){: .svg }
![](themes/sc5/images/icons/brilliant.svg){: .svg }
![](themes/sc5/images/icons/strings.svg){: .svg }
![](themes/sc5/images/icons/loop.svg){: .svg }
![](themes/sc5/images/icons/graph.svg){: .svg }
![](themes/sc5/images/icons/monkey--happy.svg){: .svg }
![](themes/sc5/images/icons/key.svg){: .svg }
![](themes/sc5/images/icons/rocket.svg){: .svg }
![](themes/sc5/images/icons/puzzle.svg){: .svg }
![](themes/sc5/images/icons/duck.svg){: .svg }
![](themes/sc5/images/icons/circles.svg){: .svg }
![](themes/sc5/images/icons/tag.svg){: .svg }
![](themes/sc5/images/icons/anchor.svg){: .svg }
![](themes/sc5/images/icons/heart.svg){: .svg }
![](themes/sc5/images/icons/mark.svg){: .svg }
![](themes/sc5/images/icons/grow.svg){: .svg }
![](themes/sc5/images/icons/toolbox.svg){: .svg }
![](themes/sc5/images/icons/dog.svg){: .svg }
![](themes/sc5/images/icons/rocket--launch.svg){: .svg }
![](themes/sc5/images/icons/arrow.svg){: .svg }
![](themes/sc5/images/icons/lambda.svg){: .svg }
![](themes/sc5/images/icons/compas.svg){: .svg }
![](themes/sc5/images/icons/propeller.svg){: .svg }
![](themes/sc5/images/icons/puzzle--turned.svg){: .svg }
![](themes/sc5/images/icons/wheel.svg){: .svg }
![](themes/sc5/images/icons/robot.svg){: .svg }
![](themes/sc5/images/icons/pile.svg){: .svg }
![](themes/sc5/images/icons/vinyl.svg){: .svg }
![](themes/sc5/images/icons/lens.svg){: .svg }
![](themes/sc5/images/icons/lips.svg){: .svg }
![](themes/sc5/images/icons/cloud.svg){: .svg }
![](themes/sc5/images/icons/cellphone.svg){: .svg }
![](themes/sc5/images/icons/pipo.svg){: .svg }
![](themes/sc5/images/icons/boat.svg){: .svg }
![](themes/sc5/images/icons/worker.svg){: .svg }
![](themes/sc5/images/icons/engineer.svg){: .svg }
![](themes/sc5/images/icons/wrench.svg){: .svg }
![](themes/sc5/images/icons/spycam.svg){: .svg }
![](themes/sc5/images/icons/pi.svg){: .svg }
![](themes/sc5/images/icons/molecule.svg){: .svg }
![](themes/sc5/images/icons/lamp.svg){: .svg }
![](themes/sc5/images/icons/cup.svg){: .svg }
![](themes/sc5/images/icons/mill.svg){: .svg }
![](themes/sc5/images/icons/vial.svg){: .svg }
![](themes/sc5/images/icons/termo.svg){: .svg }
![](themes/sc5/images/icons/excavator.svg){: .svg }
![](themes/sc5/images/icons/first-aid.svg){: .svg }
![](themes/sc5/images/icons/ketler.svg){: .svg }
![](themes/sc5/images/icons/teapot.svg){: .svg }
![](themes/sc5/images/icons/molecule--turned.svg){: .svg }
![](themes/sc5/images/icons/wrench--ring.svg){: .svg }
![](themes/sc5/images/icons/monkey--unhappy.svg){: .svg }
![](themes/sc5/images/icons/bulb--light.svg){: .svg }
![](themes/sc5/images/icons/star-treck.svg){: .svg }


## Quote in text

<blockquote markdown="1">

Digitalisaation myötä erinäisten IT palveluiden rooli muuttuu perinteisestä liiketoiminnan tukitoiminnosta
liiketoiminnan mahdollistajaksi.

</blockquote>


### Quote with sign

<figure>
  <blockquote>
    <p>Deep Learning has many different definitions depending on who you ask.</p>
  </blockquote>
  <figcaption>Max Pagels</figcaption>
</figure>


## Big quote and author
{: .slide--red .slide--shout .slide--no-title }

<figure>
  <blockquote>
    <p>One of the most common struggles in maintaining a large website, is how to implement icons.</p>
  </blockquote>
  <figcaption>Iikka Winter</figcaption>
</figure>


## Big quote
{: .slide--red .slide--shout .slide--no-title }

<blockquote markdown="1">

Fonts did a good job for a while with ability to use scalable vector graphics and css for styling, but clearly we can
see that it was just a matter of time for a better, more suitable solution to arise.

</blockquote>


## Title and subtitle

### Hei, I'm here!
{: .subtitle }


## Nested list

1. Data science
   1. Is your organization data ready?
   1. Friendly Introduction to Machine Learning
1. Development
   * Persisting Docker Volumes in ECS using EF
   * Introducing: the SC5 serverless bot workshop


## Block list

* Coffee
* Tea
  * Black tea
  * Grean tea
* Milk


## Latin and cyrillic list bullets

* How much can I expect to learn the first night?
* Which is the most difficult programming language to learn?
{: lang="en" }

* Как многому можно научиться за первую ночь?
* Какой язык программирования самый сложный?
{: lang="ru" }


## Hidden list

* Mix dry ingredients thoroughly.
* {:.next}Pour in wet ingredients
* {:.next}Mix for 10 minutes.
* {:.next}Bake for one hour at 300 degrees.


## Two columns

<div class="double" markdown="1">

Pilvipalveluita on tähän saakka tyypillisesti käytetty joko olemassa olevan konesalikapasiteetin korvaamiseen tai
laajentamiseen, jolla on saavutettu kustannushyötyjä ja joustavuutta kapasiteetin hallintaan.

Tämä on ns.
“infrastruktuuri palveluna” -pilvi (Infrastructure as a Service eli IaaS). Nämä palvelut toki auttavat kykyyn vastata
nopeammin yllättäviin resurssivaihteluihin ja mahdollistavat kustannussäästöjä kun infrastruktuuria ei tarvitse olla
“kaiken varalta” varastossa, mutta ne eivät itsessään valjasta koko pilven potentiaalia käyttöön.

</div>


## Two columns with titles

<div class="double" markdown="1">

### Apples

* Taste funny
* Cheap
* Preserve well

### Oranges

* Juicy
* Heavy
* Redundant parts

</div>


## Three columns

<div class="triple" markdown="1">

What I almost immediately noticed when I started working at SC5 was how incredibly laid back they were for being such a
professional institution. The first thing that comes to mind when you think of a consulting and web development
organization that specializes in cloud based solutions, is probably not that a couple of employees could play an
adventure time card game during their break.

</div>


## Striped Table

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |
{: .striped }


## Code listing

    <html lang="en">
    <head> <!--Comment-->
      <title>Shower</title>
      <meta charset="UTF-8">
      <link rel="stylesheet" href="screen.css">
      <script src="script.js"></script>
    </head>


## Code with highlighting

<pre><code>&lt;html lang="en"&gt;
<mark>&lt;head&gt;</mark> <span class="comment">&lt;!--Comment--&gt;</span>
	&lt;title&gt;Shower&lt;/title&gt;
	&lt;meta charset="<mark class="important">UTF-8</mark>"&gt;
	&lt;link rel="stylesheet" href="screen.css"&gt;
	&lt;script src="script.js"&gt;&lt;/script&gt;
<mark>&lt;/head&gt;</mark></code></pre>


## Highlighted code lines

<pre>
  <code>&lt;html lang="en"&gt;</code>
  <code class="mark">&lt;head&gt; <span class="comment">&lt;!--Comment--&gt;</span></code>
  <code>	&lt;title&gt;Shower&lt;/title&gt;</code>
  <code>	&lt;meta charset="<mark class="important">UTF-8</mark>"&gt;</code>
  <code>	&lt;link rel="stylesheet" href="screen.css"&gt;</code>
  <code>	&lt;script src="script.js"&gt;&lt;/script&gt;</code>
  <code class="mark">&lt;/head&gt;</code>
</pre>


## Hidden code steps
<pre>
  <code class="mark next">&lt;html lang="en"&gt;</code>
  <code>&lt;head&gt; <span class="comment">&lt;!--Comment--&gt;</span></code>
  <code class="mark next">	&lt;title&gt;Shower&lt;/title&gt;</code>
  <code>	&lt;meta charset="<mark class="important">UTF-8</mark>"&gt;</code>
  <code class="mark next">	&lt;link rel="stylesheet" href="screen.css"&gt;</code>
  <code>	&lt;script src="script.js"&gt;&lt;/script&gt;</code>
  <code class="mark next">&lt;/head&gt;</code>
</pre>


## Grid slide
{: .grid }


## One column for print
{: .slide--print }

### Subheading / Section title
{: .subtitle }

*Design strategy is a management tool to deliver world class user interfaces and enable excellent user experience. In the future, UX aspects will become naturally considered as a part of product strategy. Before this happens, it seems necessary to manage UX strategy specifically. This post reveals the secret weapon SC5 uses in designing strategy.*

Design strategy is a fairly new idea. Its emergence is a consequence of the increasing influence of design thinking among managers. The pioneering companies in both physical and digital are already using it. For other, there are no well known, public models on how to build design strategies. This is where we come in.


## Two columns for print
{: .slide--print }

### Subheading / Section title
{: .subtitle }

<div class="double" markdown="1">

### First topic

*Design strategy is a management tool to deliver world class user interfaces and enable excellent user experience. In the future, UX aspects will become naturally considered as a part of product strategy. Before this happens, it seems necessary to manage UX strategy specifically. This post reveals the secret weapon SC5 uses in designing strategy.*

### Second topic

Design strategy is a fairly new idea. Its emergence is a consequence of the increasing influence of design thinking among managers. The pioneering companies in both physical and digital are already using it. For other, there are no well known, public models on how to build design strategies. This is where we come in.

</div>


## Black slide
{: .slide--black }


## It is possible
{: #custom }

<ul class="wrapper">
  <div class="sun">
    <div class="star"></div>
  </div>
  <div class="mercury">
    <div class="planet">
      <div class="shadow"></div>
    </div>
  </div>
  <div class="venus">
    <div class="planet">
      <div class="shadow"></div>
    </div>
  </div>
  <div class="earth">
    <div class="planet"><div class="shadow"></div></div>
  </div>
  <div class="mars">
    <div class="planet"><div class="shadow"></div></div>
  </div>
  <div class="jupiter">
    <div class="planet"><div class="shadow"></div></div>
  </div>
</ul>

<style>
@keyframes spinsun {
  0% { transform: rotate(0); }
  100%   { transform: rotate(-360deg); }
}
@keyframes shadow {
  0% { background-position: 130% 0%; }
  33%{ background-position: 50% 0%; }
  55% { background-position: 0% 0%; }
  80%{ background-position: -50% 0%; }
  100%{ background-position: -50% 0%; }
}
@keyframes orbitmercury {
  0% { z-index:2; transform: rotateY(0); }
  49% { z-index:2; }
  50% { z-index:-2; }
  99% { z-index:-2; }
  100%   { z-index:2; transform: rotateY(360deg); }
}
@keyframes orbitvenus {
  0% { z-index:3; transform: rotateY(0); }
  49% { z-index:3; }
  50% { z-index:-3; }
  99% { z-index:-3; }
  100%   { z-index:3; transform: rotateY(360deg); }
}
@keyframes orbitearth {
  0% { z-index:4; transform: rotateY(0); }
  49% {z-index:4;}
  50% {z-index:-4;}
  99% {z-index:-4;}
  100%   { z-index:4; transform: rotateY(360deg);}
}
@keyframes orbitmars {
  0% { z-index:5; transform: rotateY(0); }
  49% { z-index:5; }
  50% { z-index:-5; }
  99% { z-index:-5; }
  100%   { z-index:5; transform: rotateY(360deg); }
}
@keyframes orbitjupiter {
  0% { z-index:6; transform: rotateY(270); }
  49% { z-index:6; }
  50% { z-index:-6; }
  99% { z-index:-6; }
  100%   { z-index:6; transform: rotateY(360deg); }
}
@keyframes orbitsaturn {
  0% { z-index:7; transform: rotateY(270); }
  49% { z-index:7; }
  50% { z-index:-7; }
  99% { z-index:-7; }
  100%   { z-index:7; transform: rotateY(360deg); }
}
/* Keep planet image flat */
@keyframes anti-spin {
  from { transform: rotateY(0); }
  to   { transform: rotateY(-360deg); }
}
@keyframes anti-spin-rings {
  from { transform: rotateY(0) rotateX(73deg); }
  to   { transform: rotateY(-360deg) rotateX(73deg); }
}

/* scene wrapper */
.wrapper{
  position:relative;
  margin: 0 auto;
  display:block;
  margin-top: 50px;
  perspective: 1000px;
    perspective-origin: 60% 50%;
  transform: rotate(-10deg);
  
}
.wrapper > div {
  position: relative;
  margin: 0 auto;
  transform-style: preserve-3d;
  height: 0px;
}
.sun {
  width: 250px;
  position: absolute;
  top: 0px;
  z-index: 1;
  height: 125px !important;
}
.sun .star {
  width: 250px;
  height: 250px;
  background: url(http://www.waynedunkley.com/img/solar_system/sun.png) no-repeat;
  background-size: cover;
  border-radius: 250px;
  margin: 0 auto;
  animation: spinsun 40s infinite linear;
}
.planet {
  background-size: cover;
  background-repeat: no-repeat;
  background-color: transparent;
  animation-iteration-count: infinite;
  overflow:hidden;
}
.shadow {
  position: absolute;
  left: 0px;
  right: 0px;
  top: 0px;
  bottom: 0px;
  background: transparent url(http://www.waynedunkley.com/img/solar_system/shadow.png) 0% 0% no-repeat;
  background-size: cover;
  border-radius: 100%;
}
.mercury {
  position: absolute;
  width: 400px;
  z-index:2;
  animation: orbitmercury 12s infinite linear;
  top: -7.5px; /*half of planets height to keep orbits in line*/
}
.mercury .planet {
  width:15px;
  height:15px;
  background-image: url(http://www.waynedunkley.com/img/solar_system/mercury.png);
  animation: anti-spin 12s infinite linear;
}
.mercury .shadow {
  animation: shadow 12s infinite linear;
}
.venus {
  position: absolute;
  width: 506px;
  z-index:3;
  animation: orbitvenus 15s infinite linear;
  top: -19px;
}
.venus .planet {
  width:38px;
  height:38px;
  background-image: url(http://www.waynedunkley.com/img/solar_system/venus.png);
  animation: anti-spin 15s infinite linear;
}
.venus .shadow {
  animation: shadow 15s infinite linear;
}
.earth {
  position: absolute;
  width: 610px;
  z-index:4;
  animation: orbitearth 20s infinite linear;
  top: -20px;
}
.earth .planet {
  width:40px;
  height:40px;
  background-image: url(http://www.waynedunkley.com/img/solar_system/earth.png?v=2);
  animation: anti-spin 20s infinite linear;
}
.earth .shadow {
  animation: shadow 20s infinite linear;
}
.mars {
  position: absolute;
  width: 706px;
  z-index:5;
  animation: orbitmars 30s infinite linear;
  top: -11px;
}
.mars .planet {
  width:22px;
  height:22px;
  background-image: url(http://www.waynedunkley.com/img/solar_system/mars.png);
  animation: anti-spin 30s infinite linear;
}
.mars .shadow {
  animation: shadow 30s infinite linear;
}
.jupiter {
  position: absolute;
  width: 1100px;
  z-index:6;
  animation: orbitjupiter 50s infinite linear;
  top: -64px;
}
.jupiter .planet {
  width:128px;
  height:128px;
  background-image: url(http://www.waynedunkley.com/img/solar_system/jupiter.png);
  animation: anti-spin 50s infinite linear;
}
.jupiter .shadow {
  animation: shadow 50s infinite linear;
}
</style>

## Copy & paste!

[github.com/SC5/jekyller](https://github.com/SC5/jekyller)
