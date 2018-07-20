<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Kiwi API task</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__left">
    <div class="stackedit__toc">
      
<ul>
<li><a href="#kiwi.com-promo-codes-api">Kiwi.com promo codes API</a></li>
<li><a href="#group-promo-codes">Group Promo codes</a></li>
<li><a href="#promocodes">/promocodes</a>
<ul>
<li><a href="#get">GET</a></li>
<li><a href="#put">PUT</a></li>
</ul>
</li>
</ul>

    </div>
  </div>
  <div class="stackedit__right">
    <div class="stackedit__html">
      <p>FORMAT: 1A<br>
HOST: <a href="https://promocodes.kiwi.com">https://promocodes.kiwi.com</a></p>
<h1 id="kiwi.com-promo-codes-api"><a href="http://Kiwi.com">Kiwi.com</a> promo codes API</h1>
<p><a href="http://Kiwi.com">Kiwi.com</a> promo codes API is accessible only via https to authorized users under a given set of IP addresses. This API is connected directly to our back-end and it is the recommended way how to deal with promo codes.</p>
<h1 id="group-promo-codes">Group Promo codes</h1>
<h1 id="promocodes">/promocodes</h1>
<p>Resource for retrieving information about promo codes and creating new ones.</p>
<h2 id="get">GET</h2>
<p>Returns list of all promo codes in our system with some additional information.</p>
<p><strong>Parameters of every promo code in response body:</strong></p>
<ul>
<li><em>Code</em>: string, unique alphanumeric code</li>
<li><em>BID</em>: integer, booking ID of connected booking, why promo code was created (some problem with previous booking or on which booking it was used), can be null</li>
<li><em>Used</em>: boolean, true if promo code was used</li>
<li><em>Email</em>: string, email of connected user account the promo code was created for or used by, can be null</li>
</ul>
<h3 id="response-200-json-application">Response 200 (json application)</h3>
<h4 id="body">Body</h4>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
  <span class="token string">"promocodes"</span><span class="token punctuation">:</span><span class="token punctuation">[</span>
    <span class="token punctuation">{</span>
      <span class="token string">"code"</span><span class="token punctuation">:</span><span class="token string">"AAAAQ"</span><span class="token punctuation">,</span>
      <span class="token string">"bid"</span><span class="token punctuation">:</span><span class="token keyword">null</span><span class="token punctuation">,</span>
      <span class="token string">"used"</span><span class="token punctuation">:</span><span class="token boolean">false</span><span class="token punctuation">,</span>
      <span class="token string">"amount"</span><span class="token punctuation">:</span><span class="token number">10.0</span><span class="token punctuation">,</span>
      <span class="token string">"email"</span><span class="token punctuation">:</span><span class="token string">"some@mail.com"</span>
    <span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token punctuation">{</span>
      <span class="token string">"code"</span><span class="token punctuation">:</span><span class="token string">"AAAAR"</span><span class="token punctuation">,</span>
      <span class="token string">"bid"</span><span class="token punctuation">:</span><span class="token number">123456</span><span class="token punctuation">,</span>
      <span class="token string">"used"</span><span class="token punctuation">:</span><span class="token boolean">true</span><span class="token punctuation">,</span>
      <span class="token string">"amount"</span><span class="token punctuation">:</span><span class="token number">10.0</span><span class="token punctuation">,</span>
      <span class="token string">"email"</span><span class="token punctuation">:</span> <span class="token keyword">null</span>
    <span class="token punctuation">}</span>
  <span class="token punctuation">]</span>
<span class="token punctuation">}</span>
</code></pre>
<h3 id="response-401-textplain">Response 401 (text/plain)</h3>
<pre><code>  You are not authorized for this operation.
</code></pre>
<h2 id="put">PUT</h2>
<p>Creates one promo code.<br>
<strong>Parameters for the new promo code in request body:</strong></p>
<ul>
<li><em>Code</em>: string, unique alphanumeric code</li>
<li><em>Amount</em>: integer, the amount the promo code can cover, always in EUR</li>
</ul>
<h3 id="request-json-application">Request (json application)</h3>
<h4 id="body-1">Body</h4>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
  <span class="token string">"code"</span><span class="token punctuation">:</span><span class="token string">"AAAAS"</span><span class="token punctuation">,</span>
  <span class="token string">"amount"</span><span class="token punctuation">:</span><span class="token number">10</span>
<span class="token punctuation">}</span>
</code></pre>
<h3 id="response-200-json-application-1">Response 200 (json application)</h3>
<p>In the response, the API returns the created promo code with all its details. The <code>used</code> parameter is at its default value and the parameters that can be optionally specified when promo code is used are set to <code>null</code>:</p>
<h4 id="body-2">Body</h4>
<pre class=" language-json"><code class="prism  language-json"><span class="token punctuation">{</span>
  <span class="token string">"code"</span><span class="token punctuation">:</span><span class="token string">"AAAAS"</span><span class="token punctuation">,</span>
  <span class="token string">"bid"</span><span class="token punctuation">:</span><span class="token keyword">null</span><span class="token punctuation">,</span>
  <span class="token string">"used"</span><span class="token punctuation">:</span><span class="token boolean">false</span><span class="token punctuation">,</span>
  <span class="token string">"amount"</span><span class="token punctuation">:</span><span class="token number">10.0</span><span class="token punctuation">,</span>
  <span class="token string">"email"</span><span class="token punctuation">:</span><span class="token keyword">null</span>
<span class="token punctuation">}</span>
</code></pre>

    </div>
  </div>
</body>

</html>
