---
layout: page
title: Contact
permalink: /contact/
weight: 4
---


# **How Can I Help?**

Use the form below to contact me :point_down: I'll get back to you asap :thumbs-up:

<form id="my-form"
  action="https://formspree.io/xgeykwww"
  method="POST"
>
  <label>Full Name:</label>
  <input type="text" name="fname" />

  <label>Email:</label>
  <input type="email" name="email" />

  <label>Subject:</label>
  <input type="text" name="subject" />

  <label>Message:</label>
  <input type="text" name="message" />

  <button id="my-form-button">Submit</button>   
  <p id="my-form-status"></p>
</form>

<!-- Place this script at the end of the body tag -->

<script>
  window.addEventListener("DOMContentLoaded", function() {

    // get the form elements defined in your form HTML above
    
    var form = document.getElementById("my-form");
    var button = document.getElementById("my-form-button");
    var status = document.getElementById("my-form-status");

    // Success and Error functions for after the form is submitted
    
    function success() {
      form.reset();
      button.style = "display: none ";
      status.innerHTML = "Thanks!";
    }

    function error() {
      status.innerHTML = "Oops! There was a problem.";
    }

    // handle the form submission event

    form.addEventListener("submit", function(ev) {
      ev.preventDefault();
      var data = new FormData(form);
      ajax(form.method, form.action, data, success, error);
    });
  });
  
  // helper function for sending an AJAX request

  function ajax(method, url, data, success, error) {
    var xhr = new XMLHttpRequest();
    xhr.open(method, url);
    xhr.setRequestHeader("Accept", "application/json");
    xhr.onreadystatechange = function() {
      if (xhr.readyState !== XMLHttpRequest.DONE) return;
      if (xhr.status === 200) {
        success(xhr.response, xhr.responseType);
      } else {
        error(xhr.status, xhr.response, xhr.responseType);
      }
    };
    xhr.send(data);
  }
</script>