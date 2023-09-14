<script></script>

<template>

    <li>
      <slot name="time"></slot><br>
      <slot name="date"></slot><br>
      <slot name="title"></slot><br>
      <slot name="desciption"></slot><br>
    </li>
  
  </template>
  
  <style>
  li{
    list-style-type: none;
    width: 960px;
    height: 182px;
    margin-left: 60px;
    margin-bottom: 20px;
    background-color: rgba(15, 5, 160, 1);
    color: rgb(255, 255, 255);
    padding-top: 25px;
    padding-left: 25px;
    line-height: 35px;
  }

  #desciption  {
    width: 755px;
    height: 108px;
    top: 37px;
    left: 40px;
    color: #FFBFAB,
  }

  time {
    color: rgba(235, 94, 0, 1)
  }

  .description {
    
  }
  
  </style>


