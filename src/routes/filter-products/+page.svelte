<script>
	// @ts-nocheck
  import Nav from '../../lib/Nav.svelte';
	import { onMount } from 'svelte';
  import { page } from '$app/stores';

  var setUpShopify = function(elementId, referrerId) {
    !function(t,o){function e(){var t=document.createElement("script");t.async=!0,t.src="https://sdks.shopifycdn.com/buy-button/latest/buy-button-storefront.min.js",(document.getElementsByTagName("head")[0]||document.getElementsByTagName("body")[0]).appendChild(t),t.onload=n}function n(){var e=ShopifyBuy.buildClient({domain:"shop.atalongreen.com",storefrontAccessToken:"110390f28df70a4e52acdf75d843833d"});ShopifyBuy.UI.onReady(e).then((function(e){e.createComponent("collection",{id:"294547652788",node:document.getElementById(t.toString()),moneyFormat:"%24%7B%7Bamount%7D%7D",options:{product:{styles:{product:{"@media (min-width: 601px)":{"max-width":"calc(25% - 20px)","margin-left":"20px","margin-bottom":"50px",width:"calc(25% - 20px)"},img:{height:"calc(100% - 15px)",position:"absolute",left:"0",right:"0",top:"0"},imgWrapper:{"padding-top":"calc(75% + 15px)",position:"relative",height:"0"}}},buttonDestination:"modal",contents:{options:!1},text:{button:"View product"}},productSet:{styles:{products:{"@media (min-width: 601px)":{"margin-left":"-20px"}}}},modalProduct:{contents:{img:!1,imgWithCarousel:!0,button:!1,buttonWithQuantity:!0},styles:{product:{"@media (min-width: 601px)":{"max-width":"100%","margin-left":"0px","margin-bottom":"0px"}}},text:{button:"Add to cart"}},option:{},cart:{iframe:!0,text:{total:"Subtotal",button:"Checkout"},contents:{title:!0,lineItems:!0,footer:!0},events:{afterInit:function(t){t.onCheckout=()=>{t.setNote({target:{value:o.toString()}});const e="&ref="+o.toString(),n=t.model.webUrl+e;t.checkout.open(n)}}}},toggle:{}}})}))}window.ShopifyBuy&&window.ShopifyBuy.UI?n():e()}(elementId,referrerId);
  }

	onMount(() => {
    const url = $page.url;
    const referrerId = url.searchParams.get('referrerId');
    const shopifyBuyButtonElementId = 'collection-component-1679072274745';
		setUpShopify(shopifyBuyButtonElementId, referrerId);
	});

  /* Prettified version of the Shopify Buy Button set up

(function (elementId, referrerId) {
  var scriptURL = 'https://sdks.shopifycdn.com/buy-button/latest/buy-button-storefront.min.js';
  if (window.ShopifyBuy) {
    if (window.ShopifyBuy.UI) {
      ShopifyBuyInit();
    } else {
      loadScript();
    }
  } else {
    loadScript();
  }

  function loadScript() {
    var script = document.createElement('script');
    script.async = true;
    script.src = scriptURL;
    (
      document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]
    ).appendChild(script);
    script.onload = ShopifyBuyInit;
  }
  function ShopifyBuyInit() {
    var client = ShopifyBuy.buildClient({
      domain: 'shop.atalongreen.com',
      storefrontAccessToken: '110390f28df70a4e52acdf75d843833d'
    });
    ShopifyBuy.UI.onReady(client).then(function (ui) {
      ui.createComponent('collection', {
        id: '294547652788',
        node: document.getElementById(elementId.toString()),
        moneyFormat: '%24%7B%7Bamount%7D%7D',
        options: {
          product: {
            styles: {
              product: {
                '@media (min-width: 601px)': {
                  'max-width': 'calc(25% - 20px)',
                  'margin-left': '20px',
                  'margin-bottom': '50px',
                  width: 'calc(25% - 20px)'
                },
                img: {
                  height: 'calc(100% - 15px)',
                  position: 'absolute',
                  left: '0',
                  right: '0',
                  top: '0'
                },
                imgWrapper: {
                  'padding-top': 'calc(75% + 15px)',
                  position: 'relative',
                  height: '0'
                }
              }
            },
            buttonDestination: 'modal',
            contents: {
              options: false
            },
            text: {
              button: 'View product'
            }
          },
          productSet: {
            styles: {
              products: {
                '@media (min-width: 601px)': {
                  'margin-left': '-20px'
                }
              }
            }
          },
          modalProduct: {
            contents: {
              img: false,
              imgWithCarousel: true,
              button: false,
              buttonWithQuantity: true
            },
            styles: {
              product: {
                '@media (min-width: 601px)': {
                  'max-width': '100%',
                  'margin-left': '0px',
                  'margin-bottom': '0px'
                }
              }
            },
            text: {
              button: 'Add to cart'
            }
          },
          option: {},
          cart: {
            iframe: true,
            text: {
              total: 'Subtotal',
              button: 'Checkout',
            },
            contents: {
              title: true,
              lineItems: true,
              footer: true,
            },
            events: {
              afterInit: function(cart) {
                cart.onCheckout = () => {
                  cart.setNote({target: {value: referrerId.toString()}});
                  const referrer = "&ref=" + referrerId.toString();
                  const checkoutUrl = cart.model.webUrl + referrer;
                  cart.checkout.open(checkoutUrl);
                }
              }
            }
          },
          toggle: {}
        }
      });
    });
  }
})(elementId, referrerId);

  */


</script>

<Nav />
<h1>Electrical Filter Products</h1>

<div id="collection-component-1679072274745" />