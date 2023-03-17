<script>
	// @ts-nocheck

	import { onMount } from 'svelte';

	onMount(() => {
		/*<![CDATA[*/
		(function () {
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
      let shopifyNoteModifierScript = 'setInterval(() => {' +
        'textAreaInput = document.querySelector(".shopify-buy__cart__note__text-area");' +
        'if (textAreaInput) {' +
          'textAreaInput.value = "AffiliateID123";' +
          'textAreaInput.disabled = true;' +
        '}' +
        '}, 50);';

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
						node: document.getElementById('collection-component-1679072274745'),
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
                  noteDescription: 'Attribution Code'
								},
								contents: {
                  title: true,
                  lineItems: true,
                  note: true,
                  footer: true,
                  noteModifier: true
                },
                templates: {
                  noteModifier: '<img src="https://cdn.shopify.com/s/files/1/0515/8197/6756/files/atalon-green-logo_32x32.png?v=1614315108" width="1" height="1" onload=\'' + shopifyNoteModifierScript + '\'<' + '/image>'
                },
                classes: {
                  noteModifier: 'noteModifier',
                },
                order: [
                  'title',
                  'lineItems',
                  'note',
                  'footer',
                  'noteModifier'
                ],
								events: {
									afterRender: function (cart) {
										const customDataValue = 'AffiliateID123'; // Set the custom value
                    console.log("after cart render")
									}
								}
							},
							toggle: {}
						}
					});
				});
			}
		})();
		/*]]>*/
	});
</script>

<div class="navbar">
	<div class="navbar-title"><a href="/">Atalon Green Buy Button Demo</a></div>
	<ul class="navbar-links">
		<li><a href="/residential">Residential</a></li>
		<li><a href="/commercial-lite">Commercial Lite</a></li>
		<li><a href="/commercial-heavy">Heavy Commercial</a></li>
	</ul>
</div>
<h1>Electrical Filters</h1>

<div id="collection-component-1679072274745" />