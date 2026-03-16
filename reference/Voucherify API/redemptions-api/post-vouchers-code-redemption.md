---
title: Redeem Voucher
excerpt: >-
  To redeem a voucher, you create a redemption object. It increments the
  redemption counter and updates the history of the voucher. 


  <!-- theme: danger -->

  > ❗️ Important  

  >

  > This endpoint supports the redemption of a single promo code. If you need to
  redeem more than one incentive, you can use the Stackable discounts API. The
  <!-- [stacking discounts API](OpenAPI.json/paths/~1redemptions/post)
  -->[stacking discounts API](ref:redeem-stacked-discounts) lets you redeem up
  to 5 incentives per call. Before integrating with Voucherify, choose which
  redemption endpoint you prefer to use.


  ## How discounts and order amounts are calculated in the API response?


  In the table below, you can see the logic the API follows to calculate
  discounts and amounts:


  | **Field** | **Calculation** | **Description** |

  |:---|:---|:---|

  | amount | N/A | This field shows the order amount before applying any
  discount |

  | total_amount | total_amount = amount - total_discount_amount | This field
  shows the order amount after applying all the discounts |

  | discount_amount | discount_amount = previous_discount_amount +
  applied_discount_amount | This field sums up all order-level discounts applied
  to a patricular order |

  | items_discount_amount | sum(items, i => i.discount_amount) | This field sums
  up all product-specific discounts applied to this order |

  | total_discount_amount | total_discount_amount = discount_amount +
  items_discount_amount | This field sums up all order-level and all
  product-specific discounts applied to this order |

  | applied_discount_amount | N/A | This field shows order-level discount
  applied in a particular request |

  | items_applied_discount_amount | sum(items, i => i.applied_discount_amount) |
  This field sums up all product-specific discounts applied in a particular
  request |

  | total_applied_discount_amount | total_applied_discount_amount =
  applied_discount_amount + items_applied_discount_amount | This field sums up
  all order-level and all product-specific discounts applied in a particular
  request |


  ## SDKs  


  You can invoke the redemption endpoint with one of the official libraries:  


  <!-- [![Voucherify PHP
  SDK](../docs/assets/svg/php.svg)](https://github.com/rspective/voucherify-php-sdk)&nbsp;&nbsp;

  [![Voucherify JavaScript
  SDK](../docs/assets/svg/javascript.svg)](https://github.com/rspective/voucherify.js)&nbsp;&nbsp;

  [![Voucherify Node.js
  SDK](../docs/assets/svg/nodejs.svg)](https://github.com/rspective/voucherify-nodejs-sdk)&nbsp;&nbsp;

  [![Voucherify Ruby
  SDK](../docs/assets/svg/ruby.svg)](https://github.com/rspective/voucherify-ruby-sdk)&nbsp;&nbsp;

  [![Voucherify Swift
  SDK](../docs/assets/svg/ios.svg)](https://github.com/voucherifyio/voucherify-ios-sdk)&nbsp;&nbsp;

  [![Voucherify Java
  SDK](../docs/assets/svg/java.svg)](https://github.com/rspective/voucherify-java-sdk)&nbsp;&nbsp;

  [![Voucherify Android
  SDK](../docs/assets/svg/android.svg)](https://github.com/rspective/voucherify-android-sdk)&nbsp;&nbsp;

  [![Voucherify .NET Framework
  SDK](../docs/assets/svg/dotNet.svg)](https://github.com/voucherifyio/voucherify-dotNET-sdk)&nbsp;&nbsp;

  [![Voucherify Python
  SDK](../docs/assets/svg/python.svg)](https://github.com/voucherifyio/voucherify-python-sdk)
  -->

  [block:html]

  {
    "html": "<div class=\"items\">\n\n<div class=\"item\"><a href=\"https: //github.com/rspective/voucherify-php-sdk\" target=\"_blank\"><svg xmlns=\"http: //www.w3.org/2000/svg\" width=\"42\" height=\"42\" viewBox=\"006842\" enable-background=\"new006842\"><g fill=\"#4F5B93\"><path d=\"M5115.7h-2.8l-1.57.9h2.5c1.702.8-.33.7-.9.8-.61.4-1.71.7-3.1.3-1.4.2-2.4-.4-2.9-.6-.8-1.6-1-3.2-1m-31.70h-2.8L1523.6h2.4c1.702.8-.33.7-.9s1.4-1.71.7-3.1c.3-1.4.2-2.4-.4-2.9-.5-.8-1.5-1-3.1-1\"></path><path d=\"M343.6C15.33.6011.4021s15.217.43417.4c18.7034-7.834-17.40-9.6-15.3-17.4-34-17.4zm-9.620.8c-.8.7-1.71.3-2.71.7-1.4-2.3.5-3.8.5h-3.5l-.95.1h-4l3.6-18.8H21c2.404.65.11.81.11.31.4315.2-.2.9-.51.7-.92.5-.6.6-1.11.4-1.82zm11.82.1l1.6-8.4c.2-.9.1-1.6-.2-1.9-.3-.4-1-.6-2-.6h-3.2l-210.8h-4L307.6h4l-.95.1h3.6c2.303.9.44.71.2s1.12.1.73.9l-1.78.7h-4.2zm22.4-6.7c-.2.9-.51.7-.92.5-.5.7-11.5-1.72.1-.8.7-1.71.3-2.71.7-1.3-2.3.5-3.8.5H46l-.95.1h-4l3.6-18.8h7.8c2.404.65.11.81.11.11.52.815.1z\"></path></g></svg></a></div>\n  \n<div class=\"item\"><a href=\"https: //github.com/rspective/voucherify.js\" target=\"_blank\"><svg xmlns=\"http: //www.w3.org/2000/svg\" width=\"40\" height=\"42\" viewBox=\"004042\" enable-background=\"new004042\"><path fill=\"#F8DC3C\" d=\"M38.31H1.7C.8101.802.7v36.5c01.81.71.71.7h36.5c101.7-.81.7-1.7V2.7c.1-.9-.7-1.7-1.6-1.7zM23.931.8c0.5-.11-.21.7-.1.5-.31.1-.61.6s-.7.9-1.31.2c-.5.3-1.2.4-2.1.4-1.10-2-.3-2.7-.9-.7-.6-1.1-1.3-1.4-2.3l2.3-.6c.1.4.3.8.61.1.3.3.7.41.1.4.30.6-.1.9-.2.3-.1.4-.3.5-.5.1-.3.2-.5.3-.9s.1-.7.1-1.1v-9.4h2.5v9.5zm11.32.3c-.3.5-.61-1.11.4-.4.3-1.6-1.7.9-.6.2-1.3.3-1.9.3-.90-1.8-.2-2.7-.5-.9-.3-1.6-.9-2.1-1.5l1.7-1.7c.3.4.8.91.41.1.6.31.1.41.7.4.30.60.9-.1.3-.1.6-.2.8-.3.3-.2.4-.3.6-.6.2-.3.3-.6.3-10-.3-.1-.7-.3-1-.2-.3-.4-.4-.7-.6-.3-.2-.6-.3-1-.4-.4-.1-.8-.3-1.2-.4-.4-.2-.9-.3-1.3-.4-.4-.2-.8-.4-1.1-.7-.3-.3-.6-.7-.8-1.1-.2-.4-.3-1-.3-1.7s.2-1.3.4-1.8c.3-.5.7-11.1-1.3.4-.31-.61.7-.8.6-.21.2-.31.8-.3.701.4.12.2.3.7.31.4.61.91.1l-1.71.7c-.3-.3-.6-.6-1.1-.9-.5-.3-1-.3-1.5-.3-.30-.60-.9.1-.3.1-.5.2-.8.3-.3.2-.4.3-.6.6-.2.3-.3.5-.3.9s.1.6.2.8c.2.3.3.4.5.6.3.2.5.3.9.4.3.1.7.31.3.4.2.9.31.4.5.5.21.41.3.7.4.3.7.711.1s.31.31.7c.51.31.702.2z\"></path></svg></a></div>\n\n<div class=\"item\"><a href=\"https: //github.com/rspective/voucherify-nodejs-sdk\" target=\"_blank\"><svg xmlns=\"http: //www.w3.org/2000/svg\" width=\"39\" height=\"42\" viewBox=\"003942\" enable-background=\"new003942\"><path fill=\"#8FC84F\" d=\"M17.8.5c1-.62.4-.63.405.2310.55.915.78.91.61.61.71.62.8V30c01.2-.72.3-1.82.8-5.22.9-10.45.9-15.68.8-1.1.6-2.4.6-3.5-.1-1.6-.9-3.1-1.8-4.7-2.7-.3-.2-.7-.3-.9-.7.2-.3.6-.3.8-.4.7-.21.3-.51.9-.9.2-.1.3-.1.501.3.82.71.642.3.3.2.6-.1.8-.25.1-2.910.2-5.815.4-8.7.2-.1.3-.3.3-.5V12.1c0-.2-.1-.5-.3-.5C30.28.7255.719.82.8c-.2-.1-.4-.1-.60C145.78.88.73.611.6c-.2.1-.4.3-.3.5v17.6c0.2.1.4.3.5l4.22.4c.8.41.7.72.6.3.8-.31.3-11.3-1.9V13.5c0-.3.2-.5.5-.4h2c.30.5.3.4.5v17.6c01.6-.63.3-2.14-1.8.9-4.7-5.8-.2-1.5-.8-3-1.7-4.5-2.5-1-.5-1.8-1.7-1.8-2.8V12.2c0-1.2.7-2.31.7-2.85.2-310.5-5.915.7-8.9zM22.412.9c2.3-.14.7-.16.811.6.92.52.72.54.40.2-.3.4-.5.4h-2c-.30-.4-.2-.5-.5-.2-.8-.6-1.7-1.4-2.1-1.2-.6-2.6-.6-4-.6-1.1-2.1-2.8.7-.6.4-.81.3-.62.2.5.8.71.3.82.7.75.6.68.31.61.1.42.21.12.62.3.51.6.33.4-.84.7-.91-2.21.6-3.51.9-1.7.4-3.6.4-5.3.2-1.7-.2-3.4-.6-4.7-1.8-1.1-1-1.6-2.4-1.6-3.90-.2.3-.4.5-.4h2c.30.5.2.5.5.1.8.41.61.12.11.4.93.84.6.81.3-.12.7-.13.8-.9.6-.5.7-1.3.6-2-.2-.6-.8-.9-1.3-1-2.7-.9-5.6-.5-8.3-1.5-1.1-.4-2.1-1.1-2.6-2.2-.6-1.6-.3-3.5.9-4.81-1.12.8-1.64.4-1.7z\"></path></svg></a></div>\n\n<div class=\"item\"><a href=\"https: //github.com/rspective/voucherify-ruby-sdk\" target=\"_blank\"><svg xmlns=\"http: //www.w3.org/2000/svg\" width=\"38\" height=\"42\" viewBox=\"003842\" enable-background=\"new003842\"><path fill=\"#CC342D\" d=\"M1.421.6c.3-.8.5-2.31.2-3.63.2-6.58.2-11.214.7-14.11.3-.62.8-.84.2-.81.802.91.23.13.1.9.11.9-.32.8-3.18.4-914-17.417.2-.3.1-.7.2-1.2-2.7.5-4.5-1.1-4.5-4.7zm21.8-6.3c4.5-.39.1-.713.8-1l-.8-.8C32.110.328723.93.6c-.4-.3-.7-.8-1.2-1.6h4.6c1.703.5-.25.1.23.6.75.635.56.7-.13.5-.46.9-.710.4-.45.3-.810.5-1.215.8-.1.9-.21.9-.32.9-1.9-1.7-3.7-3.4-5.6-5-.3-.3-.4-.5-.7-.7-2.2-1.4-3.1-3.5-3.6-6.1-.7-3.3-1.6-6.6-2.4-9.9-.1-.2-.1-.5-.2-1zM635.5c1-.21.9-.22.8-.4.3-.1.8-.5.8-.8.8-2.61.6-5.22.4-7.9.1-.3.2-.4.3-.84.81.59.5314.44.6-2.52.6-5.24.7-8.36.75.4.410.8.816.11.3v.2c-1.2.1-2.4.2-3.5.3-6.8.4-13.6.9-20.51.3-1.1-.1-2.20-3.30-4.6-.1-7.2-2.6-7.2-7.20-2.6.3-5.2.4-7.80-.2.3-.3.4-.6.3.2.6.3.7.6l49.6c.2.3.3.5.5.9z\"></path></svg></a></div>\n\n\n<div class=\"item\"><a href=\"https: //github.com/voucherifyio/voucherify-ios-sdk\" target=\"_blank\"><svg xmlns=\"http: //www.w3.org/2000/svg\" width=\"40\" height=\"42\" viewBox=\"004042\" enable-background=\"new004042\"><path fill=\"#F47B3A\" d=\"M31.11H8.9C410509.9v22.3C0374418.941h22.3c4.908.9-48.9-8.9V9.9C40536131.11zm2.732.7s-1.6-2.6-4.2-2.6c-2.50-42.6-92.6-11.20-16.5-9.4-16.5-9.410.16.6171.9171.9-4.6-2.6-14.3-15.3-14.3-15.38.57.312.29.212.29.2-2.2-1.8-8.3-10.5-8.3-10.54.9514.611.814.611.82.6-7.2-2.1-13.7-2.6-14.313.198.918.88.918.8s3.74.12.27.8z\"></path><path fill=\"#DD6631\" d=\"M4.224.4c10.16.6171.9171.9C16.623.76.9116.911c8.47.212.19.112.19.1-2.2-1.8-8.3-10.5-8.3-10.54.9514.611.814.611.8C2814.1237.522.77.1l-.1-.1-5.8-6H8.9C410509.9V20l4.24.4c-.10-.1000\"></path></svg></a></div>\n\n<div class=\"item\"><a href=\"https: //github.com/rspective/voucherify-java-sdk\" target=\"_blank\"><svg xmlns=\"http: //www.w3.org/2000/svg\" width=\"32\" height=\"42\" viewBox=\"003242\" enable-background=\"new003242\"> <path fill=\"#E92D2F\" stroke=\"#E92D2F\" stroke-width=\".094\" stroke-miterlimit=\"10\" d=\"M20.20c.91.11.32.714-.31.6-1.23-2.24.2-.81-1.81.8-2.82.7-1.2.9-2.31.9-33.3-.61.1-.82.4-.33.5.722.33.43.25.3-.9-.8-1.9-1.8-2.8-2.7-.9-1-1.8-2-2.4-3.3-.4-.8-.6-1.8-.3-2.8.3-.9.9-1.71.6-2.41.8-1.84.1-3.26-5.11-11.8-2.32.1-3.7.2-.9.1-2-.1-3zm-1.511.7c2-1.44.3-2.46.6-3.1-1.81.2-3.82.3-5.43.8-.6.6-1.21.2-1.42-.2.6-.11.3.11.8.411.21.81.72.7.5.8.61.8.22.6-.51.2-1.62.1-2.72.8-.2.1-.3.3-.4.3.8-.71.3-1.61.3-2.60-.8-.4-1.4-.9-1.9-1-1.2-1.8-2.8-1.7-4.4.1-1.81.3-3.12.6-4z\"></path> <path fill=\"#0774BA\" stroke=\"#0774BA\" stroke-width=\".094\" stroke-miterlimit=\"10\" d=\"M25.723.5c.4-.51.1-.71.8-.81.1-.22.3.23.8.7.61.11.5.92.4-.21.1-.81.9-1.72.6-1.41.2-3.21.8-52.3l.3-.3c1.3-.82.7-1.63.7-2.8.6-.81.1-1.7.8-2.7-.2-1.1-1.3-1.9-2.4-2-.4.2-.9.3-1.4.5zm-20.6.9c1.8-.83.9-1.36-1.3-1.2.3-2.4.7-3.51.2-.3.2-.6.3-.8.60.1.2.3.3.3.7.31.4.32.2.42.6.25.2.17.9-.12.6-.25.1-.57.6-.9-.6.3-1.2.5-1.7.8-.3.2-.6.3-.9.3-3.1.7-6.4.9-9.6.9-1.30-2.40-3.7-.1-1.3-.1-2.8-.2-4.1-.6-.2.1-.50-.8-.3-.2-.1-.2-.30-.5.3-.3.7-.51.1-.7zm2.54.4c.5-.41.2-.71.8-.8-.2.3-.5.5-.5.80.3.2.4.3.5.3.2.8.31.1.31.9.23.9.36.21.8-.13.6-.45.4-.7.5.41.1.81.71.1-2.2.7-4.41-6.61.2-2.1.2-4.3.2-6.4-.2-.8-.2-1.7-.3-2.4-.8-.3-.2-.7-.4-.8-.80-.4.1-.6.4-.8zm1.14.4c.5-.41.1-.61.6-.8-.2.2-.5.4-.3.7.3.3.8.41.2.51.8.33.4.35.2.31.3-.12.6-.33.9-.5.8.41.5.82.31.1-1.2.5-2.5.9-3.81.2-2.2.4-4.4.4-6.6.1-1-.2-1.9-.4-2.9-.8-.3-.2-.7-.4-.8-.8-.2-.40-.8.2-1zm-5.62.9c.9-.31.9-.62.9-.6.40.801.2.3-1.2.1-2.4.3-3.4.9-.3.2-.5.3-.6.60.3.3.4.6.51.5.63.1.84.6.94.6.49.3.313.9-.21.8-.23.5-.45.2-.8.5-.21.2-.31.5-.8.3-.3.1-.7-.2-.9.3.2.8.4.8.9-.2.5-.7.8-11-1.3.7-2.81-4.21.3-4.2.8-8.41-12.7.8-3.2-.1-6.4-.4-9.6-.9-.6-.2-1.2-.3-1.6-.7-.3-.30-.8.3-.9.6-.71.5-1.12.3-1.4zm25.53.5c1-.32.1-.82.9-1.6-.2.9-.91.5-1.71.9-1.4.8-3.11.1-4.71.4-3.4.5-6.9.7-10.3.6-2.4-.1-4.8-.2-7.1-.7-.6-.2-1.2-.3-1.7-.62.1.34.2.56.3.63.4.16.9010.3-.42-.24-.66-1.2z\"></path></svg></a></div>\n\n<div class=\"item\"><a href=\"https: //github.com/rspective/voucherify-android-sdk\" target=\"_blank\"><svg xmlns=\"http: //www.w3.org/2000/svg\" width=\"36\" height=\"42\" viewBox=\"003642\" enable-background=\"new003642\"> <path fill=\"#a4c828\" d=\"M35.625.5c01.4-1.12.4-2.42.4s-2.4-1.1-2.4-2.4V14.6c0-1.41.1-2.42.4-2.4s2.41.12.42.4v10.9zm-30.30c01.4-1.12.4-2.42.4S.526.8.525.5V14.6c0-1.41.1-2.42.4-2.4s2.41.12.42.4v10.9zM23.63.1L25.5.3c0-.10-.2-.2-.3-.1-.1-.3-.1-.30l-22.8c-1.3-.5-3-.8-5-.8s-3.7.3-5.1.8l-2-2.8c0-.1-.20-.30-.1.1-.2.2-.2.3l22.7c-5.72.5-5.88.6-5.88.6h22.9c-.10-.3-6.1-5.9-8.5M138.1c-.80-1.4-.6-1.4-1.4s.6-1.41.4-1.41.4.61.41.4c0.7-.61.4-1.41.4m100c-.80-1.4-.6-1.4-1.4s.6-1.41.4-1.41.4.61.41.4c0.7-.71.4-1.41.4\"></path> <path fill=\"#a4c828\" d=\"M29.513h-23v19.2c0.8.61.41.41.4h3v6c01.41.12.42.42.4s2.4-1.12.4-2.4v-6.1h4.6v6.1c01.41.12.42.42.4s2.4-1.12.4-2.4v-6.1h3c.801.4-.61.4-1.4V13z\"></path> </svg></a></div>\n\n<div class=\"item\"><a href=\"https: //github.com/voucherifyio/voucherify-dotNET-sdk\" target=\"_blank\"><svg xmlns=\"http: //www.w3.org/2000/svg\" viewBox=\"00128128\" width=\"42\" height=\"42\"><path fill-rule=\"evenodd\" clip-rule=\"evenodd\" fill=\"#1384C8\" d=\"M82.10878.432c.479-1.2321.022-2.4451.427-3.7012.288-7.0974.554-14.26.805-21.309.865-2.7311.813-5.423.515-7.7672.692-3.7096.442-5.65210.88-6.3311.741-.2663.518-.3895.28-.4065.267-.0510.536-.01515.804-.01.280.56.029.957.052-.129.304-.199.525-.311.724-1.9553.494-3.8727.009-5.88510.468-3.5056.022-7.01612.042-10.63117.998-2.3193.819-4.8347.52-7.68710.974-2.1052.548-4.3214.984-7.1466.77-1.9251.217-3.9811.929-6.3151.917-8.278-.045-16.556-.012-24.834-.024-2.461-.004-4.568-.941-6.356-2.603-2.563-2.381-4.093-5.412-5.345-8.608-2.284-5.835-3.563-11.951-5.031-18.014-.688-2.838-1.47-5.654-2.215-8.478-.048-.183-.142-.354-.25-.617l-.577.542c-3.2283.207-6.0716.741-8.61510.498-.6931.024-.9262.374-1.3133.591-1.4244.47-2.7228.983-4.26413.411-1.4774.242-4.1257.616-8.2649.61-2.421.165-5.0041.795-7.6891.855-3.98.088-7.962.098-11.943.134-.952.009-.996-.069-.748-.991.707-6.3383.87-12.5146.58-18.4922.794-6.1676.085-12.04810.231-17.4192.823-3.6575.941-7.0319.843-9.5821.979-1.2934.083-2.3156.477-2.584.394-.045.793-.0731.189-.0738.478-.00416.956.08225.433-.0394.547-.0657.8391.85510.3045.5151.5332.2762.634.7613.5537.3281.8615.1783.01810.5474.32515.878.7483.0511.5816.0812.3799.12.06.228.157.446.238.668l.199-.006z\"/></svg></a></div>\n\n<div class=\"item\"><a href=\"https: //github.com/voucherifyio/voucherify-python-sdk\" target=\"_blank\"><svg xmlns=\"http: //www.w3.org/2000/svg\" viewBox=\"00128128\" width=\"42\" height=\"42\"><linearGradient id=\"a\" gradientUnits=\"userSpaceOnUse\" x1=\"70.252\" y1=\"1237.476\" x2=\"170.659\" y2=\"1151.089\" gradientTransform=\"matrix(.56300-.568-29.215707.817)\"><stop offset=\"0\" stop-color=\"#5A9FD4\"/><stop offset=\"1\" stop-color=\"#306998\"/></linearGradient><path fill=\"url(#a)\" d=\"M63.3911.988c-4.222.02-8.252.379-11.81.007-10.451.846-12.3465.71-12.34612.837v9.411h24.693v3.137h-33.961c-7.1760-13.464.313-15.42612.521-2.2689.405-2.36815.275025.0961.7557.3115.94712.51913.12412.519h8.491v-11.282c0-8.1517.051-15.3415.426-15.34h24.665c6.866012.346-5.65412.346-12.548v-23.513c0-6.693-5.646-11.72-12.346-12.837-4.244-.706-8.645-1.027-12.866-1.008zm-13.3547.569c2.5504.6342.1174.6344.72102.593-2.0834.69-4.6344.69-2.560-4.633-2.097-4.633-4.69-.001-2.6042.073-4.7214.633-4.721z\"/><linearGradient id=\"b\" gradientUnits=\"userSpaceOnUse\" x1=\"209.474\" y1=\"1098.811\" x2=\"173.62\" y2=\"1149.537\" gradientTransform=\"matrix(.56300-.568-29.215707.817)\"><stop offset=\"0\" stop-color=\"#FFD43B\"/><stop offset=\"1\" stop-color=\"#FFE873\"/></linearGradient><path fill=\"url(#b)\" d=\"M91.68228.38v10.966c08.5-7.20815.655-15.42615.655h-24.665c-6.7560-12.3465.783-12.34612.549v23.515c06.6915.81810.62812.34612.5477.8162.29715.3122.71324.66506.216-1.80112.346-5.42312.346-12.547v-9.412h-24.664v-3.138h37.012c7.17609.852-5.00512.348-12.5192.578-7.7352.467-15.1740-25.096-1.774-7.145-5.161-12.521-12.348-12.521h-9.268zm-13.87359.547c2.56104.6342.0974.6344.69202.602-2.0744.719-4.6344.719-2.550-4.633-2.117-4.633-4.7190-2.5952.083-4.6924.633-4.692z\"/><radialGradient id=\"c\" cx=\"1825.678\" cy=\"444.45\" r=\"26.743\" gradientTransform=\"matrix(0-.24-1.0550532.979557.576)\" gradientUnits=\"userSpaceOnUse\"><stop offset=\"0\" stop-color=\"#B8B8B8\" stop-opacity=\".498\"/><stop offset=\"1\" stop-color=\"#7F7F7F\" stop-opacity=\"0\"/></radialGradient><path opacity=\".444\" fill=\"url(#c)\" enable-background=\"new\" d=\"M97.309119.597c03.543-14.8166.416-33.0916.416-18.2760-33.092-2.873-33.092-6.4160-3.54414.815-6.41733.092-6.41718.275033.0912.87233.0916.417z\"/></svg></a></div>\n</div>\n\n<style>\n.items\n{\n    display: table;\n    width: 50%;\n}\n.item\n{\n    display:table-cell;\n}\n</style>"
  }

  [/block]


  ## Customer tracking


  The redeem operation is a key part of [Customer tracking]
  (doc:customer-tracking) workflow. There're 3 ways you can identify your end
  customer in Voucherify within this request. You can either provide a tracking
  ID (e.g. your customer's login or a generated id), a customer ID (if the
  customer is already stored in Voucherify) or a full `customer` object in the
  payload. Note that you can pass and thus store any customer-related metadata.
  See examples on the right.


  <!--

  title: "Example Customer"

  lineNumbers: true

  -->

  ```json

  "customer": {
    "source_id": "alice.morgan",
    "name": "Alice Morgan",
    "email": "alice@morgan.com",
    "description": "",
    "metadata": {
      "locale": "en-GB",
      "shoeSize": 5,
      "favourite_brands": ["Armani", "L’Autre Chose", "Vicini"]
    }
  }

  ```


  If you already created a customer profile in Voucherify's database, whether it
  was implicitly by providing it to the redeem function or explicitly by
  invoking the <!-- [Create Customer](OpenAPI.json/paths/~1customers/post)
  -->[Create Customer](ref:create-customer) method, you can identify your
  customer in redemptions by a generated ID (starting with `cust_`). 


  <!--

  lineNumbers: true

  -->

  ```json title=Example Customer Identifier [object]

  "customer": {
      "id": "cust_C9qJ3xKgZFqkpMw7b21MF2ow"
  }

  ```

  <!--

  lineNumbers: true

  -->

  ```json title=Example Customer Identifier

  {
    "customer": "cust_C9qJ3xKgZFqkpMw7b21MF2ow"
  }

  ```

  <!--

  lineNumbers: true

  -->

  ```json title=Example Customer Identifier by Source ID

  {
    "customer": "alice.morgan"
  }

  ```


  <!-- theme: info -->

  > 📘 Redemption rollback

  >

  > Do you need to undo a redemption? You can do it with <!-- [redemption
  rollback](OpenAPI.json/paths/~1redemptions~1{redemptionId}~1rollback/post)
  -->[redemption rollback](ref:rollback-redemption).


  ## Redemption failures


  There are several reasons why a redemption may fail. You will get the reason
  in the error key:
   - `resource_not_found` - voucher with given code does not exist
  - `voucher_not_active` - voucher is not active yet (before start date)

  - `voucher_expired` - voucher has already expired (after expiration date)

  - `voucher_disabled` -  voucher has been disabled (`active: false`)

  - `quantity_exceeded` - voucher's redemptions limit has been exceeded

  - `gift_amount_exceeded` - gift amount has been exceeded

  - `customer_rules_violated` - customer did not match the segment

  - `order_rules_violated` - order did not match validation rules

  - `invalid_order` - order was specified incorrectly

  - `invalid_amount` - order amount was specified incorrectly

  - `missing_amount` - order amount was not specified

  - `missing_order_items` - order items were not specified

  - `missing_customer` - customer was not specified


  ## Order object


  The purchase of previously defined products (products are stored in
  Voucherify) by end customers is handled through the order object. You are
  obligated to pass the order object in case you use validation rules. You can
  learn more about the [validation rules structure] (doc:validation-rules).  


  | **Attributes** | **Description** |

  |:---|:---|

  | amount<br>`integer` | A positive integer representing the total amount for
  the order. |

  | items<br>`list` | List of items constituting the order. Order items can be
  defined either by `product_id` or `sku_id`. Along with every item you must
  define the `quantity`.<br><br>Child attributes:<br><br>- `product_id`
  (*string*) - The ID of the associated product object for this line
  item.<br><br>- `sku_id` (*string*) - The ID of the associated variant (sku)
  object for this line item.<br><br>- `quantity` (*integer*) - A positive
  integer representing the number of instances of the item that are included in
  this order line.<br><br>- `price` (*integer*) - A positive integer
  representing the cost of an item.<br><br>- `amount` (*integer*) - `quantity` *
  `price` (you should provide it to retrieve `discount_amount` for a particular
  order item if the discount is applied only to this item learn more |



  <!-- theme: info -->


  > 🚧 Order ID

  >

  > If you use the same order id in more than one redemption request, all valid
  discounts provided in the redemption payload will be applied to the given
  order. [Read more in this guide]
  (https://docs.voucherify.io/docs/manage-stackable-discounts).


  <!--

  lineNumbers: true

  -->

  ```json title=Example Order

  "order": {
    "amount": 10000,
    "items": [
      {
        "product_id": "prod_Bi7sRr3kwvxH2I",
        "quantity": 1
      }
    ]
  }

  ```

  ## Gift Vouchers - redeem Gift Card and control redeemed amount


  In Voucherify,you can also create a gift card for customers. Customers then
  can use gift card credits to fulfill the order. A user can specify how many
  credits he wants to use from the gift card. The available balance of credits
  is counted based on policy rules attached to the Gift Voucher definition.


  When the user wants to define how many gift credits are to be used from the
  gift card to complete the order, the `credits` property can be assigned the
  equivalent value in the lowest currency in the request body. The value of
  credits being applied to the order cannot be higher than the current balance
  on the gift card.


  <!--

  lineNumbers: true

  -->

  ```cURL title=Example Request - control redeemed amount

  curl -i -X POST \
     -H "Content-Type:application/json" \
     -H "X-App-Id:c70a6f00-cf91-4756-9df5-47628850002b" \
     -H "X-App-Token:3266b9f8-e246-4f79-bdf0-833929b1380c" \
     -d '{
          "order": {
             "amount": 2500
          },
          "gift": {
             "credits": 1500
          }
        }' \ 
   'https://api.voucherify.io/v1/vouchers/aDm4CRR3/redemption'
  ```

  ## Loyalty Coins - redeem loyalty card and pay with points


  Voucherify offers the possibility to set up a reward type in the Loyalty
  Program, which allows using loyalty points as gift credits. The available
  balance of credits is counted based on policy rules attached to the reward
  definition.


  If a user configures just one reward type of paying in points, in the
  redemption request, there is no additional information required. Voucherify
  will automatically select as a proper reward definition and will calculate the
  discount based on the attached policy.  


  <!--

  lineNumbers: true

  -->

  ```json title=Example Request

  {
      "order": {
          "amount": 25000,
          "items": [
              {
                  "product_id": "test_source_1",
                  "quantity": "1",
                  "price": 15000
              },
              {
                  "product_id": "test_source_2",
                  "quantity": "1",
                  "price": 10000
              }
          ]
      },
      "metadata": {
          "category": "vip",
          "shop": "s1",
          "location": "l1"
      }
  }

  ```

  <!--

  lineNumbers: true

  -->

  ```json title=Example Response

  {
      "id": "r_zv5Qn7cF68RbVX4foKxgwUi1",
      "object": "redemption",
      "date": "2020-05-24T13:44:20Z",
      "customer_id": "cust_lXisxEaEHYKTEVf1YnNS8AUh",
      "amount": 250,
      "order": {
          "status": "PROCESSING",
          "items": [
              {
                  "object": "order_item",
                  "product_id": "test_source_1",
                  "quantity": 1,
                  "amount": 15000,
                  "price": 15000
              },
              {
                  "object": "order_item",
                  "product_id": "test_source_2",
                  "quantity": 1,
                  "amount": 10000,
                  "price": 10000
              }
          ],
          "customer": {
              "id": "cust_lXisxEaEHYKTEVf1YnNS8AUh",
              "object": "customer",
              "referrals": {
                  "campaigns": [],
                  "total": 0
              }
          },
          "amount": 25000,
          "object": "order",
          "id": "ord_Tgi2ApelDyl86sm5AYDKCBMZ",
          "created_at": "2020-05-24T13:44:20Z",
          "discount_amount": 25000
      },
      "customer": {
          "id": "cust_lXisxEaEHYKTEVf1YnNS8AUh",
          "source_id": "tom+Loyalty@email.com",
          "name": "Tom Loyalty",
          "email": "tom+Loyalty@email.com",
          "metadata": {},
          "object": "customer"
      },
      "reward": {
          "assignment_id": "rewa_pHilLjHWOD7oNjJZnog3VoEi",
          "loyalty_tier_id": "ltr_3q5dW6GaRC4QkA1oYmfGy1k1",
          "id": "rew_3qmzGPWJ7LfLXnPAjmbPacIl",
          "name": "1 point - 25 cents",
          "created_at": "2020-05-22T18:39:52Z",
          "updated_at": "2020-05-23T08:18:55Z",
          "parameters": {
              "automation_id": null,
              "coin": {
                  "exchange_ratio": 0.25
              }
          },
          "type": "COIN",
          "object": "reward"
      },
      "metadata": {
          "category": "vip",
          "shop": "s1",
          "location": "l1"
      },
      "result": "SUCCESS",
      "tracking_id": "track_IWQYtuUE7phYpPzTHD5uwbyvlrO4nqyzipbQQtsHrRw=",
      "voucher": {
          "id": "v_wjgLC2lrQy1urPOdd35JX0RtkcOcQOmb",
          "code": "Dm1x8MuX",
          "campaign": "TestLoyalty-GivePoints",
          "campaign_id": "camp_qVVaC4vpVlof03eBi8qb5gE7",
          "category": null,
          "type": "LOYALTY_CARD",
          "discount": null,
          "gift": null,
          "loyalty_card": {
              "points": 489,
              "balance": 23
          },
          "start_date": null,
          "expiration_date": null,
          "validity_timeframe": null,
          "validity_day_of_week": null,
          "publish": {
              "object": "list",
              "count": 1,
              "url": "/v1/vouchers/Dm1x8MuX/publications?page=1&limit=10"
          },
          "redemption": {
              "object": "list",
              "quantity": null,
              "redeemed_quantity": 8,
              "url": "/v1/vouchers/Dm1x8MuX/redemptions?page=1&limit=10",
              "redeemed_points": 466
          },
          "active": true,
          "additional_info": null,
          "metadata": {},
          "assets": {
              "qr": {
                  "id": "U2FsdGVkX1+9Eo0bLWMZmYK6nQxl3AyR3nqkloGURcpRJcxL3hl5xXSGRYjYdySc9twLaKnYGVXbLtjCGW8FBotl1rTAxLJQm4okoJ385Gd6pc1ty6AnhaHHJjCeLoYYSQCG1EyP9PRxnTihjmsE9g==",
                  "url": "https://dev.dl.voucherify.io/api/v1/assets/qr/U2FsdGVkX1%2B9Eo0bLWMZmYK6nQxl3AyR3nqkloGURcpRJcxL3hl5xXSGRYjYdySc9twLaKnYGVXbLtjCGW8FBotl1rTAxLJQm4okoJ385Gd6pc1ty6AnhaHHJjCeLoYYSQCG1EyP9PRxnTihjmsE9g%3D%3D"
              },
              "barcode": {
                  "id": "U2FsdGVkX19NfR0ANlhLM7Df9Ec+xqTh6aTbHakk/Gzeh9zTiuj8KUBLswVXkz0gdLVnn1ZtzjCv7oF/BSQTyJx0YSK+HIUG9RGD+9rVhiC7+4WkSKrgAZ+NeqQBIqcespt8WWygXjfkvbyXBSF7Lg==",
                  "url": "https://dev.dl.voucherify.io/api/v1/assets/barcode/U2FsdGVkX19NfR0ANlhLM7Df9Ec%2BxqTh6aTbHakk%2FGzeh9zTiuj8KUBLswVXkz0gdLVnn1ZtzjCv7oF%2FBSQTyJx0YSK%2BHIUG9RGD%2B9rVhiC7%2B4WkSKrgAZ%2BNeqQBIqcespt8WWygXjfkvbyXBSF7Lg%3D%3D"
              }
          },
          "is_referral_code": false,
          "holder_id": "cust_lXisxEaEHYKTEVf1YnNS8AUh",
          "updated_at": "2020-05-24T13:44:20Z",
          "holder": {
              "id": "cust_lXisxEaEHYKTEVf1YnNS8AUh",
              "source_id": "tom+Loyalty@email.com",
              "name": "Tom Loyalty",
              "email": "tom+Loyalty@email.com",
              "metadata": {},
              "object": "customer"
          },
          "object": "voucher",
          "validation_rules_assignments": {
              "data": [],
              "object": "list",
              "total": 0,
              "data_ref": "data"
          }
      }
  }

  ```


  In case the user wants to define how much he spends in points, it is
  configurable by property `points` in a request body.


  <!--

  lineNumbers: true

  -->

  ```json title=Example Request

  {
      "reward": {
          "points": 10
      },
      "order": {
          "amount": 25000,
          "items": [
              {
                  "product_id": "test_source_1",
                  "quantity": "1",
                  "price": 15000
              },
              {
                  "product_id": "test_source_2",
                  "quantity": "1",
                  "price": 10000
              }
          ]
      },
      "metadata": {
          "category": "vip",
          "shop": "s1",
          "location": "l1"
      }
  }

  ```

  <!--

  lineNumbers: true

  -->

  ```json title=Example Response

  {
      "id": "r_NJIfNYD8uc2lNm3YBAqXr3FF",
      "object": "redemption",
      "date": "2020-05-24T16:28:29Z",
      "customer_id": "cust_lXisxEaEHYKTEVf1YnNS8AUh",
      "amount": 10,
      "order": {
          "status": "PROCESSING",
          "items": [
              {
                  "object": "order_item",
                  "product_id": "test_source_1",
                  "quantity": 1,
                  "amount": 15000,
                  "price": 15000
              },
              {
                  "object": "order_item",
                  "product_id": "test_source_2",
                  "quantity": 1,
                  "amount": 10000,
                  "price": 10000
              }
          ],
          "customer": {
              "id": "cust_lXisxEaEHYKTEVf1YnNS8AUh",
              "object": "customer",
              "referrals": {
                  "campaigns": [],
                  "total": 0
              }
          },
          "amount": 25000,
          "object": "order",
          "id": "ord_70kKdXIKCSx5cfglKSpz9aHy",
          "created_at": "2020-05-24T16:28:29Z",
          "discount_amount": 250
      },
      "customer": {
          "id": "cust_lXisxEaEHYKTEVf1YnNS8AUh",
          "source_id": "tom+Loyalty@email.com",
          "name": "Tom Loyalty",
          "email": "tom+Loyalty@email.com",
          "metadata": {},
          "object": "customer"
      },
      "reward": {
          "assignment_id": "rewa_pHilLjHWOD7oNjJZnog3VoEi",
          "loyalty_tier_id": null,
          "id": "rew_3qmzGPWJ7LfLXnPAjmbPacIl",
          "name": "1 point - 25 cents",
          "created_at": "2020-05-22T18:39:52Z",
          "updated_at": "2020-05-24T13:44:26Z",
          "parameters": {
              "automation_id": null,
              "coin": {
                  "exchange_ratio": 0.25
              }
          },
          "type": "COIN",
          "object": "reward"
      },
      "metadata": {
          "category": "vip",
          "shop": "s1",
          "location": "l1"
      },
      "result": "SUCCESS",
      "tracking_id": "track_IWQYtuUE7phYpPzTHD5uwbyvlrO4nqyzipbQQtsHrRw=",
      "voucher": {
          "id": "v_wjgLC2lrQy1urPOdd35JX0RtkcOcQOmb",
          "code": "Dm1x8MuX",
          "campaign": "TestLoyalty-GivePoints",
          "campaign_id": "camp_qVVaC4vpVlof03eBi8qb5gE7",
          "category": null,
          "type": "LOYALTY_CARD",
          "discount": null,
          "gift": null,
          "loyalty_card": {
              "points": 539,
              "balance": 63
          },
          "start_date": null,
          "expiration_date": null,
          "validity_timeframe": null,
          "validity_day_of_week": null,
          "publish": {
              "object": "list",
              "count": 1,
              "url": "/v1/vouchers/Dm1x8MuX/publications?page=1&limit=10"
          },
          "redemption": {
              "object": "list",
              "quantity": null,
              "redeemed_quantity": 9,
              "url": "/v1/vouchers/Dm1x8MuX/redemptions?page=1&limit=10",
              "redeemed_points": 476
          },
          "active": true,
          "additional_info": null,
          "metadata": {},
          "assets": {
              "qr": {
                  "id": "U2FsdGVkX1+9Eo0bLWMZmYK6nQxl3AyR3nqkloGURcpRJcxL3hl5xXSGRYjYdySc9twLaKnYGVXbLtjCGW8FBotl1rTAxLJQm4okoJ385Gd6pc1ty6AnhaHHJjCeLoYYSQCG1EyP9PRxnTihjmsE9g==",
                  "url": "https://dev.dl.voucherify.io/api/v1/assets/qr/U2FsdGVkX1%2B9Eo0bLWMZmYK6nQxl3AyR3nqkloGURcpRJcxL3hl5xXSGRYjYdySc9twLaKnYGVXbLtjCGW8FBotl1rTAxLJQm4okoJ385Gd6pc1ty6AnhaHHJjCeLoYYSQCG1EyP9PRxnTihjmsE9g%3D%3D"
              },
              "barcode": {
                  "id": "U2FsdGVkX19NfR0ANlhLM7Df9Ec+xqTh6aTbHakk/Gzeh9zTiuj8KUBLswVXkz0gdLVnn1ZtzjCv7oF/BSQTyJx0YSK+HIUG9RGD+9rVhiC7+4WkSKrgAZ+NeqQBIqcespt8WWygXjfkvbyXBSF7Lg==",
                  "url": "https://dev.dl.voucherify.io/api/v1/assets/barcode/U2FsdGVkX19NfR0ANlhLM7Df9Ec%2BxqTh6aTbHakk%2FGzeh9zTiuj8KUBLswVXkz0gdLVnn1ZtzjCv7oF%2FBSQTyJx0YSK%2BHIUG9RGD%2B9rVhiC7%2B4WkSKrgAZ%2BNeqQBIqcespt8WWygXjfkvbyXBSF7Lg%3D%3D"
              }
          },
          "is_referral_code": false,
          "holder_id": "cust_lXisxEaEHYKTEVf1YnNS8AUh",
          "updated_at": "2020-05-24T16:28:29Z",
          "holder": {
              "id": "cust_lXisxEaEHYKTEVf1YnNS8AUh",
              "source_id": "tom+Loyalty@email.com",
              "name": "Tom Loyalty",
              "email": "tom+Loyalty@email.com",
              "metadata": {},
              "object": "customer"
          },
          "object": "voucher",
          "validation_rules_assignments": {
              "data": [],
              "object": "list",
              "total": 0,
              "data_ref": "data"
          }
      }
  }

  ```


  Moreover, it is possible to define many levels of reward in which collected
  points can be used as gift credits. Per each tier, we can implement different
  conversion factors. Having many options in the rewards catalog, we will need
  to select a coins calculation policy (reward ID) that we want to use for
  calculating a final discount in the redemption request.



  <!--

  lineNumbers: true

  -->

  ```json title=Example Request

  {
      "reward": {
          "points": 30,
          "id": "rew_noP2S5H8PEBFT97mennSA531"
      },
      "order": {
          "amount": 25000,
          "items": [
              {
                  "product_id": "test_source_1",
                  "quantity": "1",
                  "price": 15000
              },
              {
                  "product_id": "test_source_2",
                  "quantity": "1",
                  "price": 10000
              }
          ]
      },
      "metadata": {
          "category": "vip",
          "shop": "s1",
          "location": "l1"
      }
  }

  ```

  <!--

  lineNumbers: true

  -->

  ```json title=Example Response

  {
      "id": "r_se17sLon6YX5wMhYVzfQa2dc",
      "object": "redemption",
      "date": "2020-05-24T13:41:16Z",
      "customer_id": "cust_lXisxEaEHYKTEVf1YnNS8AUh",
      "amount": 10,
      "order": {
          "status": "PROCESSING",
          "items": [
              {
                  "object": "order_item",
                  "product_id": "test_source_1",
                  "quantity": 1,
                  "amount": 15000,
                  "price": 15000
              },
              {
                  "object": "order_item",
                  "product_id": "test_source_2",
                  "quantity": 1,
                  "amount": 10000,
                  "price": 10000
              }
          ],
          "customer": {
              "id": "cust_lXisxEaEHYKTEVf1YnNS8AUh",
              "object": "customer",
              "referrals": {
                  "campaigns": [],
                  "total": 0
              }
          },
          "amount": 25000,
          "object": "order",
          "id": "ord_EfMmve84JzQIg2MCM3cAvLgF",
          "created_at": "2020-05-24T13:41:16Z",
          "discount_amount": 25000
      },
      "customer": {
          "id": "cust_lXisxEaEHYKTEVf1YnNS8AUh",
          "source_id": "tom+Loyalty@email.com",
          "name": "Tom Loyalty",
          "email": "tom+Loyalty@email.com",
          "metadata": {},
          "object": "customer"
      },
      "reward": {
          "assignment_id": "rewa_g3QQwQfhJrjBYzEa1NJkub7N",
          "loyalty_tier_id": null,
          "id": "rew_noP2S5H8PEBFT97mennSA531",
          "name": "1 point 25$",
          "created_at": "2020-05-24T12:57:19Z",
          "parameters": {
              "automation_id": null,
              "coin": {
                  "exchange_ratio": 25.0
              }
          },
          "type": "COIN",
          "object": "reward"
      },
      "metadata": {
          "category": "vip",
          "shop": "s1",
          "location": "l1"
      },
      "result": "SUCCESS",
      "tracking_id": "track_IWQYtuUE7phYpPzTHD5uwbyvlrO4nqyzipbQQtsHrRw=",
      "voucher": {
          "id": "v_wjgLC2lrQy1urPOdd35JX0RtkcOcQOmb",
          "code": "Dm1x8MuX",
          "campaign": "TestLoyalty-GivePoints",
          "campaign_id": "camp_qVVaC4vpVlof03eBi8qb5gE7",
          "category": null,
          "type": "LOYALTY_CARD",
          "discount": null,
          "gift": null,
          "loyalty_card": {
              "points": 439,
              "balance": 223
          },
          "start_date": null,
          "expiration_date": null,
          "validity_timeframe": null,
          "validity_day_of_week": null,
          "publish": {
              "object": "list",
              "count": 1,
              "url": "/v1/vouchers/Dm1x8MuX/publications?page=1&limit=10"
          },
          "redemption": {
              "object": "list",
              "quantity": null,
              "redeemed_quantity": 7,
              "url": "/v1/vouchers/Dm1x8MuX/redemptions?page=1&limit=10",
              "redeemed_points": 216
          },
          "active": true,
          "additional_info": null,
          "metadata": {},
          "assets": {
              "qr": {
                  "id": "U2FsdGVkX1+9Eo0bLWMZmYK6nQxl3AyR3nqkloGURcpRJcxL3hl5xXSGRYjYdySc9twLaKnYGVXbLtjCGW8FBotl1rTAxLJQm4okoJ385Gd6pc1ty6AnhaHHJjCeLoYYSQCG1EyP9PRxnTihjmsE9g==",
                  "url": "https://dev.dl.voucherify.io/api/v1/assets/qr/U2FsdGVkX1%2B9Eo0bLWMZmYK6nQxl3AyR3nqkloGURcpRJcxL3hl5xXSGRYjYdySc9twLaKnYGVXbLtjCGW8FBotl1rTAxLJQm4okoJ385Gd6pc1ty6AnhaHHJjCeLoYYSQCG1EyP9PRxnTihjmsE9g%3D%3D"
              },
              "barcode": {
                  "id": "U2FsdGVkX19NfR0ANlhLM7Df9Ec+xqTh6aTbHakk/Gzeh9zTiuj8KUBLswVXkz0gdLVnn1ZtzjCv7oF/BSQTyJx0YSK+HIUG9RGD+9rVhiC7+4WkSKrgAZ+NeqQBIqcespt8WWygXjfkvbyXBSF7Lg==",
                  "url": "https://dev.dl.voucherify.io/api/v1/assets/barcode/U2FsdGVkX19NfR0ANlhLM7Df9Ec%2BxqTh6aTbHakk%2FGzeh9zTiuj8KUBLswVXkz0gdLVnn1ZtzjCv7oF%2FBSQTyJx0YSK%2BHIUG9RGD%2B9rVhiC7%2B4WkSKrgAZ%2BNeqQBIqcespt8WWygXjfkvbyXBSF7Lg%3D%3D"
              }
          },
          "is_referral_code": false,
          "holder_id": "cust_lXisxEaEHYKTEVf1YnNS8AUh",
          "updated_at": "2020-05-24T13:41:16Z",
          "holder": {
              "id": "cust_lXisxEaEHYKTEVf1YnNS8AUh",
              "source_id": "tom+Loyalty@email.com",
              "name": "Tom Loyalty",
              "email": "tom+Loyalty@email.com",
              "metadata": {},
              "object": "customer"
          },
          "object": "voucher",
          "validation_rules_assignments": {
              "data": [],
              "object": "list",
              "total": 0,
              "data_ref": "data"
          }
      }
  }

  ```
api:
  file: voucherify-api.json
  operationId: post-vouchers-code-redemption
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---