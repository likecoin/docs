---
description: >-
  This page is showing how to use query string to change ISCN badge Looks in
  color and size.
---

# ISCN Badge

**You can add one of the following query string after the "`?`" of the Base URL below. Base URL:**   
`https://static.like.co/badge/iscn/<iscn_tx_hash>.svg?`

Success Example: [https://static.like.co/badge/iscn/dev/976F3D3D32F32B2496E5D48273A61080F08F8C3A40F7EFDB878519107787DF12.svg?dark=1&responsive=0&width=82](https://static.like.co/badge/iscn/dev/976F3D3D32F32B2496E5D48273A61080F08F8C3A40F7EFDB878519107787DF12.svg?dark=1&responsive=0&width=82)

<table>
  <thead>
    <tr>
      <th style="text-align:left">Query String</th>
      <th style="text-align:left">Accepted Value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">dark</td>
      <td style="text-align:left">
        <p>boolean. e.g. 0 (light) or 1 (dark)</p>
        <p>When not provided, default to 0.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">responsive</td>
      <td style="text-align:left">
        <p>boolean. e.g. 0 (size is not responsive) or 1 (responsive size)</p>
        <p>When not provided, default to 0.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">width</td>
      <td style="text-align:left">
        <p>number. e.g. 164 (164px)</p>
        <p>When not provided, default to 164.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">height</td>
      <td style="text-align:left">
        <p>number. e.g. 64 (64px)</p>
        <p>When not provided, default to 64.</p>
      </td>
    </tr>
  </tbody>
</table>

**Some errors may happened when providing multiple conflicting query string values between responsive, width, and height.**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Error Scenario</th>
      <th style="text-align:left">Error Code &amp; Explanation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">responsive=1&amp;width=30</td>
      <td style="text-align:left">400
        <br />Does not know whether the user want a fixed size or responsive size.</td>
    </tr>
    <tr>
      <td style="text-align:left">responsive=1&amp;height=20</td>
      <td style="text-align:left">400
        <br />Does not know whether the user want a fixed size or responsive size.</td>
    </tr>
    <tr>
      <td style="text-align:left">responsive=0&amp;height=sf</td>
      <td style="text-align:left">
        <p>400</p>
        <p>Height in wrong format (NaN).</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">responsive=0&amp;wodth=sf</td>
      <td style="text-align:left">
        <p>400</p>
        <p>Height in wrong format (NaN).</p>
      </td>
    </tr>
  </tbody>
</table>

**Note:** 

When providing both height & width, but the ratio does not fit to 164 \(width\) \* 64 \(height\), we will anchor the size of the badge on **width**.  
For example, user provides `width=200&height=400`, the overall size for the badge would be: `width=200&height=200*64/164`.



