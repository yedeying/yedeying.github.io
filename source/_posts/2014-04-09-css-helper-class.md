---
layout: post
title: "CSS helper class"
date: 2014-04-09 14:08:01 +0800
comments: true
categories:
- css
tags:
- css
---
应该习惯的css helper class
<table class="width-100" style="height: 520px; width: 672px;">
  <style>
    .width-100 {
      border-collapse: collapse;
    }
    .width-100 td {
      border: 1px solid #aaa;
    }
  </style>
  <tbody>
    <tr>
      <td class="nowrap">
        <code>.text-centered</code></td>
      <td class="width-100">text-align: center;</td>
    </tr>
    <tr>
      <td><code>.text-right</code></td>
      <td>text-align: right;</td>
    </tr>
    <tr>
      <td><code>.small</code></td>
      <td>small font size from variables.less</td>
    </tr>
    <tr>
      <td><code>.last</code></td>
      <td>margin-right: 0;</td>
    </tr>
    <tr>
      <td><code>.pause</code></td>
      <td>margin-bottom: baseline/2;</td>
    </tr>
    <tr>
      <td><code>.end</code></td>
      <td>margin-bottom: 0;</td>
    </tr>
    <tr>
      <td><code>.normal</code></td>
      <td>font-weight: normal;</td>
    </tr>
    <tr>
      <td><code>.bold</code></td>
      <td>font-weight: bold;</td>
    </tr>
    <tr>
      <td><code>.italic</code></td>
      <td>font-style: italic;</td>
    </tr>
    <tr>
      <td><code>.group</code></td>
      <td>clearfix layer</td>
    </tr>
    <tr>
      <td><code>.right</code></td>
      <td>float: right;</td>
    </tr>
    <tr>
      <td><code>.left</code></td>
      <td>float: left;</td>
    </tr>
    <tr>
      <td><code>.nowrap</code></td>
      <td>white-space: nowrap;</td>
    </tr>
    <tr>
      <td><code>.req</code>&nbsp;
        <code>.required</code></td>
      <td>font-weight: normal; + red color from variables.less</td>
    </tr>
    <tr>
      <td><code>.success</code></td>
      <td>green color from variables.less</td>
    </tr>
    <tr>
      <td><code>.error</code></td>
      <td>red color from variables.less</td>
    </tr>
    <tr>
      <td><code>.color-gray</code></td>
      <td>color: #777;</td>
    </tr>
    <tr>
      <td class="nowrap">
        <code>.color-gray-light</code></td>
      <td>color: #999;</td>
    </tr>
    <tr>
      <td><code>.color-black</code></td>
      <td>color: #000;</td>
    </tr>
    <tr>
      <td><code>.color-red</code></td>
      <td>red color from variables.less</td>
    </tr>
    <tr>
      <td><code>.color-green</code></td>
      <td>green color from variables.less</td>
    </tr>
    <tr>
      <td><code>.no-wrap-line</code></td>
      <td>overflow: hidden;text-overflow: ellipsis;white-space: nowrap;display: block</td>
    </tr>
  </tbody>
</table>

