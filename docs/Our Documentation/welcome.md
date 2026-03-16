---
title: welcome
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
test beans beans beans

| saf        | ff  | ff |
| :--------- | :-- | :- |
| asasfsfasf | asf |    |
| sfsf       | asf |    |

beans beans beans beans

[block:html]
{
  "html": "<div class=\"chlog-box\">\n    <div class=\"from-area\">\n        <span class=\"from-label\">Effective from:</span><br>\n        <span class=\"from-date\">May 19, 2023</span>\n    </div>\n    <div class=\"change-area\">\n      \n      <p>We have improved the validation for products and deal-products endpoints to ensure that the API behavior works as explained in our API Reference for a consistent and reliable experience.</p>\n      \n      <b><p>We kindly ask you to review the documentation for <a href=\"https://developers.pipedrive.com/docs/api/v1/Products\">Products API</a> and <a href=\"https://developers.pipedrive.com/docs/api/v1/Deals\">deal-products endpoints</a> and update your API consumption logic if necessary.</p></b>\n      \n      <br>\n      <p>We will be providing a 30-day window for reviewing the following logic for products and deal-products endpoints:</p>\n      \n      <b><h3>1. Getting the list of products attached to a deal</h3></b>\n      <p>For the <code><a href=\"https://developers.pipedrive.com/docs/api/v1/Deals#getDealProducts\">GET /deals/{id}/products</a></code> endpoint, the <code>include_product_data</code> query parameter only supports numerical values 1 and 0:</p>\n      <ul>\n        <li>1 – for retrieving the product data along with each attached product</li>\n        <li>0 – for not retrieving the product data. This is the default value for the parameter</li>\n      </ul>\n      \n      <br>\n      <b><h3>2. Adding and updating products</h3></b>\n      \n      <p>For the <code><a href=\"https://developers.pipedrive.com/docs/api/v1/Products#addProduct\">POST /products</a></code> and <code><a href=\"https://developers.pipedrive.com/docs/api/v1/Products#updateProduct\">PUT /products/{id}</a></code> endpoints, the <code>prices</code> body parameter needs to be supplied as an array of objects containing:</p>\n      <ul>\n        <li><code>currency</code> (string) - a required field</li>\n        <li><code>price</code> (number) – a required field</li>\n        <li><code>cost</code> (number) – optional</li>\n        <li><code>overhead_cost</code> (number) – optional</li>\n      </ul>\n      <br>\n      <p>Please note that there can only be one price per product per currency. When the <code>prices</code> parameter is omitted altogether, a default price of 0 and a default currency based on the company’s currency will be assigned.</p>\n      \n      <p>Here’s an example of a PUT payload where one product price (<code>\"id\": 10</code>) is being updated and another price is being created:</p>\n      <div class=\"CodeTabs CodeTabs_initial theme-undefined\"><div class=\"CodeTabs-toolbar\"><button type=\"button\">json</button></div><div class=\"CodeTabs-inner\"><pre><button aria-label=\"Copy Code\" class=\"rdmd-code-copy fa\"></button><code class=\"rdmd-code lang-json theme-light\" data-lang=\"json\" name=\"json\"><div class=\"cm-s-neo\">{\n  <span class=\"cm-property\">\"name\"</span>: <span class=\"cm-string\">\"My product\"</span>,\n  <span class=\"cm-property\">\"prices\"</span>: [\n     {\n         <span class=\"cm-property\">\"id\"</span>: <span class=\"cm-number\">10</span>,\n         <span class=\"cm-property\">\"currency\"</span>: <span class=\"cm-string\">\"EUR\"</span>,\n         <span class=\"cm-property\">\"price\"</span>: <span class=\"cm-number\">20</span>,\n         <span class=\"cm-property\">\"cost\"</span>: <span class=\"cm-number\">2</span>\n     },\n     {\n         <span class=\"cm-property\">\"currency\"</span>: <span class=\"cm-string\">\"USD\"</span>,\n         <span class=\"cm-property\">\"price\"</span>: <span class=\"cm-number\">15</span>,\n         <span class=\"cm-property\">\"cost\"</span>: <span class=\"cm-number\">8</span>\n     }\n   ]\n}\n</div></code></pre></div></div>\n      \n      <br>\n      <b><h3>3. Adding and updating deal-products</h3></b>\n      \n      <p>For the <code><a href=\"https://developers.pipedrive.com/docs/api/v1/Deals#addDealProduct\">POST /deals/{id}/products</a></code> and <code><a href=\"https://developers.pipedrive.com/docs/api/v1/Deals#updateDealProduct\">PUT /deals/{id}/products/{product_attachment_id}</a></code> endpoints, the required body parameters and their data types are as follows:</p>\n      <ul>\n        <li><code>product_id</code> (integer)</li>\n        <li><code>item_price</code> (number)</li>\n        <li><code>quantity</code> (integer)</li>\n      </ul>\n      \n      <br>\n      <p>The optional body parameters and their data types are:</p>\n      <ul>\n        <li><code>discount_percentage</code> (number) – If omitted, the default value is 0</li>\n        <li><code>duration</code> (number) – If omitted, the default value is 1</li>\n      </ul>\n      \n      <br>\n      <p>For the full list of optional parameters, please refer to the documentation of the POST and PUT endpoints.</p>\n \n      <p>If you have any questions or comments, let us know in <a href=\"https://devcommunity.pipedrive.com/\">the Developer’s Community</a>.</p>\n      \n    \n      </div>\n</div>"
}
[/block]

```
<div class="chlog-box">
    <div class="from-area">
        <span class="from-label">Effective from:</span><br>
        <span class="from-date">May 19, 2023</span>
    </div>
    <div class="change-area">
      
      <p>We have improved the validation for products and deal-products endpoints to ensure that the API behavior works as explained in our API Reference for a consistent and reliable experience.</p>
      
      <b><p>We kindly ask you to review the documentation for <a href="https://developers.pipedrive.com/docs/api/v1/Products">Products API</a> and <a href="https://developers.pipedrive.com/docs/api/v1/Deals">deal-products endpoints</a> and update your API consumption logic if necessary.</p></b>
      
      <br>
      <p>We will be providing a 30-day window for reviewing the following logic for products and deal-products endpoints:</p>
      
      <b><h3>1. Getting the list of products attached to a deal</h3></b>
      <p>For the <code><a href="https://developers.pipedrive.com/docs/api/v1/Deals#getDealProducts">GET /deals/{id}/products</a></code> endpoint, the <code>include_product_data</code> query parameter only supports numerical values 1 and 0:</p>
      <ul>
        <li>1 – for retrieving the product data along with each attached product</li>
        <li>0 – for not retrieving the product data. This is the default value for the parameter</li>
      </ul>
      
      <br>
      <b><h3>2. Adding and updating products</h3></b>
      
      <p>For the <code><a href="https://developers.pipedrive.com/docs/api/v1/Products#addProduct">POST /products</a></code> and <code><a href="https://developers.pipedrive.com/docs/api/v1/Products#updateProduct">PUT /products/{id}</a></code> endpoints, the <code>prices</code> body parameter needs to be supplied as an array of objects containing:</p>
      <ul>
        <li><code>currency</code> (string) - a required field</li>
        <li><code>price</code> (number) – a required field</li>
        <li><code>cost</code> (number) – optional</li>
        <li><code>overhead_cost</code> (number) – optional</li>
      </ul>
      <br>
      <p>Please note that there can only be one price per product per currency. When the <code>prices</code> parameter is omitted altogether, a default price of 0 and a default currency based on the company’s currency will be assigned.</p>
      
      <p>Here’s an example of a PUT payload where one product price (<code>"id": 10</code>) is being updated and another price is being created:</p>
      <div class="CodeTabs CodeTabs_initial theme-undefined"><div class="CodeTabs-toolbar"><button type="button">json</button></div><div class="CodeTabs-inner"><pre><button aria-label="Copy Code" class="rdmd-code-copy fa"></button><code class="rdmd-code lang-json theme-light" data-lang="json" name="json"><div class="cm-s-neo">{
  <span class="cm-property">"name"</span>: <span class="cm-string">"My product"</span>,
  <span class="cm-property">"prices"</span>: [
     {
         <span class="cm-property">"id"</span>: <span class="cm-number">10</span>,
         <span class="cm-property">"currency"</span>: <span class="cm-string">"EUR"</span>,
         <span class="cm-property">"price"</span>: <span class="cm-number">20</span>,
         <span class="cm-property">"cost"</span>: <span class="cm-number">2</span>
     },
     {
         <span class="cm-property">"currency"</span>: <span class="cm-string">"USD"</span>,
         <span class="cm-property">"price"</span>: <span class="cm-number">15</span>,
         <span class="cm-property">"cost"</span>: <span class="cm-number">8</span>
     }
   ]
}
</div></code></pre></div></div>
      
      <br>
      <b><h3>3. Adding and updating deal-products</h3></b>
      
      <p>For the <code><a href="https://developers.pipedrive.com/docs/api/v1/Deals#addDealProduct">POST /deals/{id}/products</a></code> and <code><a href="https://developers.pipedrive.com/docs/api/v1/Deals#updateDealProduct">PUT /deals/{id}/products/{product_attachment_id}</a></code> endpoints, the required body parameters and their data types are as follows:</p>
      <ul>
        <li><code>product_id</code> (integer)</li>
        <li><code>item_price</code> (number)</li>
        <li><code>quantity</code> (integer)</li>
      </ul>
      
      <br>
      <p>The optional body parameters and their data types are:</p>
      <ul>
        <li><code>discount_percentage</code> (number) – If omitted, the default value is 0</li>
        <li><code>duration</code> (number) – If omitted, the default value is 1</li>
      </ul>
      
      <br>
      <p>For the full list of optional parameters, please refer to the documentation of the POST and PUT endpoints.</p>
 
      <p>If you have any questions or comments, let us know in <a href="https://devcommunity.pipedrive.com/">the Developer’s Community</a>.</p>
      
    
      </div>
</div>
```