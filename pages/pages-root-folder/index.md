---
#
# Use the widgets beneath and the content will be
# inserted automagically in the webpage. To make
# this work, you have to use › layout: frontpage
#
layout: frontpage
header:
  image_fullwidth: head.png
widget1:
  title: "О сайте"
  url: '/info/'
  #image: widget-1-302x182.jpg
  text: 'Добро пожаловать на страничку сообщества Yandex DataSphere в образовании и научных исследованиях! Здесь вы найдёте всю необходимую информацию о том, как начать использовать DataSphere в учебном процессе, включая серию <a href="/quickstarts">серию вводных видео</a>, <a href="https://github.com/yandex-datasphere">примеры кода</a> и многое другое. Задать свои вопросы и пообщаться с коллегами можно <a href="http://t.me/yandex-datasphere">в телеграм-канале</a>' 
widget2:
  title: "Вводные видео"
  url: '/quickstart/'
  text: 'В этой серии коротких видео мы расскажем вам, что такое Yandex DataSphere, и как начать использовать её в образовательном процессе и научных исследованиях.'
  video: '<a href="#" data-reveal-id="videoModal"><img src="/images/intro_video.png" alt=""/></a>'
widget3:
  title: "Документация"
  url: 'https://cloud.yandex.ru/docs/datasphere/'
  image: datasphere_logo.jpg
  text: 'Официальная документация - это всегда самый достоверный и актуальный источник информации о продукте!'
#
# Use the call for action to show a button on the frontpage
#
# To make internal links, just use a permalink like this
# url: /getting-started/
#
# To style the button in different colors, use no value
# to use the main color or success, alert or secondary.
# To change colors see sass/_01_settings_colors.scss
#
callforaction:
  url: https://github.com/yandex-datasphere
  text: Наш GitHub ›
  style: alert
permalink: /index.html
#
# This is a nasty hack to make the navigation highlight
# this page as active in the topbar navigation
#
homepage: true
---

<div id="videoModal" class="reveal-modal large" data-reveal="">
  <div class="flex-video widescreen vimeo" style="display: block;">
    <iframe width="1280" height="720" src="https://www.youtube.com/embed/EKulOpdn8BQ" frameborder="0" allowfullscreen></iframe>
  </div>
  <a class="close-reveal-modal">&#215;</a>
</div>
