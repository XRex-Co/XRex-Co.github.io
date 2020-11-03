---
layout: default
title: 購入
---
aaa
<input type="text" id="name" name="name"/>

<form action="https://formspree.io/f/{form_id}" method="post">
  <label for="email">Your Email</label>
  <input name="Email" id="email" type="email">
  <button type="submit">Submit</button>
</form>

<div id="contact">
        <h2>Get in Touch</h2>
        <div id="contact-form">
                <form action="https://formspree.io/mpzyqdng" method="POST">
                <input type="hidden" name="_subject" value="Contact request from personal website" />
                <input type="email" name="_replyto" placeholder="Your email" required>
                <textarea name="message" placeholder="Type your message" required></textarea>
                <button type="submit">Send</button>
            </form>
        </div>
    </div>

<form action="https://credit.j-payment.co.jp/gateway/payform.aspx"method="POST">
<input type="hidden"name="aid"value="119743">
<input type="hidden"name="pt"value="1">
<input type="hidden"name="cmd"value="0">
<input type="hidden"name="jb"value="CAPTURE">
<input type="hidden"name="am"value="1000">
<input type="hidden"name="tx"value="10">
<input type="hidden"name="sf"value="0">
<input type="submit"name="submit"value="購入">
</form> 
