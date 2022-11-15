---

excalidraw-plugin: parsed
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠==


# Text Elements
Memory Management ^uoCEqVIf

Separate Virtual and Physical
    Allocators! ^VGdUjpsj

Heap Implementation ^yWowMrpD

Will require a mapper
for mapping the two together ^XYCMSnOd

Allows for dynamic allocation
(Not limited to 4KiB size) ^VlmdJ7a7

Two parts ^aGwbwaK7

Header ^gNdjLqH5

Data ^AZV0DdfN

Header needs to store next heap,
previous heap, size ^WMsu8jA7

Use of Frifgg to do this
for us. ^11lQtgGe

Load memory map given by
bootloader
 ^7rfJ6nEc

User Mode ^XViZK2Xj

Only allocate a couple pages if needed ^AUPgYfwl

Then when needed (Page Fualt)
give a page and returnt to the process ^Sj2JaFBD

%%
# Drawing
```json
{
	"type": "excalidraw",
	"version": 2,
	"source": "https://excalidraw.com",
	"elements": [
		{
			"type": "text",
			"version": 72,
			"versionNonce": 555705961,
			"isDeleted": false,
			"id": "uoCEqVIf",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -173.93331909179688,
			"y": -394.54586029052734,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 352,
			"height": 46,
			"seed": 1552891430,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [
				{
					"id": "n_iVP_2Zi9jgmL0e_gsO1",
					"type": "arrow"
				},
				{
					"id": "fGBZhqb1Sy_uUcR5pQa7l",
					"type": "arrow"
				},
				{
					"id": "B8blZ6edopem0n7OAFBUw",
					"type": "arrow"
				},
				{
					"id": "kT10PVKDY_gaN53BCJKvC",
					"type": "arrow"
				}
			],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"fontSize": 36,
			"fontFamily": 1,
			"text": "Memory Management",
			"rawText": "Memory Management",
			"baseline": 32,
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "Memory Management"
		},
		{
			"type": "arrow",
			"version": 172,
			"versionNonce": 264196263,
			"isDeleted": false,
			"id": "n_iVP_2Zi9jgmL0e_gsO1",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 30.333801780259137,
			"y": -401.76574174032163,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 44.99463792245297,
			"height": 75.22535295124214,
			"seed": 1692161190,
			"groupIds": [],
			"strokeSharpness": "round",
			"boundElements": [],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "uoCEqVIf",
				"focus": 0.053709022183761494,
				"gap": 7.219881449794286
			},
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					44.99463792245297,
					-75.22535295124214
				]
			]
		},
		{
			"type": "text",
			"version": 61,
			"versionNonce": 1259909449,
			"isDeleted": false,
			"id": "VGdUjpsj",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 83.76499465565485,
			"y": -521.7370570420745,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 415,
			"height": 70,
			"seed": 1337686138,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [
				{
					"id": "a56GsTHqYrjVuIqxpBpne",
					"type": "arrow"
				}
			],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 1,
			"text": "Separate Virtual and Physical\n    Allocators!",
			"rawText": "Separate Virtual and Physical\n    Allocators!",
			"baseline": 60,
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "Separate Virtual and Physical\n    Allocators!"
		},
		{
			"type": "arrow",
			"version": 31,
			"versionNonce": 352101319,
			"isDeleted": false,
			"id": "fGBZhqb1Sy_uUcR5pQa7l",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 40.87967247605428,
			"y": -343.41340214699215,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 42.885450910230816,
			"height": 123.03214367535173,
			"seed": 480741670,
			"groupIds": [],
			"strokeSharpness": "round",
			"boundElements": [],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "uoCEqVIf",
				"focus": -0.15763113210128762,
				"gap": 5.132458143535189
			},
			"endBinding": {
				"elementId": "yWowMrpD",
				"focus": -0.747704749172637,
				"gap": 1
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					42.885450910230816,
					123.03214367535173
				]
			]
		},
		{
			"type": "text",
			"version": 37,
			"versionNonce": 1097179177,
			"isDeleted": false,
			"id": "yWowMrpD",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 59.15871396080928,
			"y": -220.22652259019878,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 280,
			"height": 35,
			"seed": 1842900646,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [
				{
					"id": "fGBZhqb1Sy_uUcR5pQa7l",
					"type": "arrow"
				},
				{
					"id": "VQiSXvymRWZNJOHU3F_HE",
					"type": "arrow"
				},
				{
					"id": "q3eW0yLiLjgDQJAY1pwFj",
					"type": "arrow"
				}
			],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 1,
			"text": "Heap Implementation",
			"rawText": "Heap Implementation",
			"baseline": 25,
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "Heap Implementation"
		},
		{
			"type": "arrow",
			"version": 101,
			"versionNonce": 694325991,
			"isDeleted": false,
			"id": "a56GsTHqYrjVuIqxpBpne",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 253.02271973698237,
			"y": -528.8888126929428,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 88.77590341187829,
			"height": 216.63238916304886,
			"seed": 2127996353,
			"groupIds": [],
			"strokeSharpness": "round",
			"boundElements": [],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "VGdUjpsj",
				"focus": -0.09350953552256488,
				"gap": 7.151755650868267
			},
			"endBinding": {
				"elementId": "XYCMSnOd",
				"focus": 0.10129498552833173,
				"gap": 10.494266785002765
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-88.77590341187829,
					-216.63238916304886
				]
			]
		},
		{
			"type": "text",
			"version": 118,
			"versionNonce": 32617225,
			"isDeleted": false,
			"id": "XYCMSnOd",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -36.46381811501874,
			"y": -827.0154686409944,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 407,
			"height": 70,
			"seed": 666541985,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [
				{
					"id": "a56GsTHqYrjVuIqxpBpne",
					"type": "arrow"
				}
			],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 1,
			"text": "Will require a mapper\nfor mapping the two together",
			"rawText": "Will require a mapper\nfor mapping the two together",
			"baseline": 60,
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "Will require a mapper\nfor mapping the two together"
		},
		{
			"type": "arrow",
			"version": 47,
			"versionNonce": 360553991,
			"isDeleted": false,
			"id": "VQiSXvymRWZNJOHU3F_HE",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 252.05764711295126,
			"y": -176.6802844011399,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 206.98281139803964,
			"height": 81.05620586216935,
			"seed": 1098481743,
			"groupIds": [],
			"strokeSharpness": "round",
			"boundElements": [],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "yWowMrpD",
				"focus": 0.07370285757945094,
				"gap": 8.546238189058897
			},
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					206.98281139803964,
					81.05620586216935
				]
			]
		},
		{
			"type": "rectangle",
			"version": 64,
			"versionNonce": 1094216169,
			"isDeleted": false,
			"id": "JMW-wZw9ME46qbQXZ539I",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 469.65502055577724,
			"y": -150.14401180555413,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 224.8344463362663,
			"height": 55.967387600185674,
			"seed": 1063584097,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [],
			"updated": 1668541269892,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 114,
			"versionNonce": 1548371239,
			"isDeleted": false,
			"id": "x-q6ZlmruFaIlK-cEGRdg",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 471.58490077107786,
			"y": -87.42195510756324,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 222.42211815320388,
			"height": 183.34144746965796,
			"seed": 1177257263,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [
				{
					"id": "xLlMKco5WQWxjmlaqm3es",
					"type": "arrow"
				}
			],
			"updated": 1668541269892,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 47,
			"versionNonce": 407192777,
			"isDeleted": false,
			"id": "CJSvr017S18ntp75OYns-",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 468.69003627600034,
			"y": 104.60408584732716,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 226.7644148958201,
			"height": 45.835339781351195,
			"seed": 477398543,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [],
			"updated": 1668541269892,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 100,
			"versionNonce": 1832192071,
			"isDeleted": false,
			"id": "_6_IsD1gH0I0pxTwbNaaN",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 462.41785931808363,
			"y": 161.53639146909978,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 235.4489200367991,
			"height": 15.439306755164353,
			"seed": 926118095,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [],
			"updated": 1668541269892,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 229,
			"versionNonce": 1924383657,
			"isDeleted": false,
			"id": "VlmdJ7a7",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 707.5163571198921,
			"y": -104.26425185017945,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 396,
			"height": 70,
			"seed": 44327329,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 1,
			"text": "Allows for dynamic allocation\n(Not limited to 4KiB size)",
			"rawText": "Allows for dynamic allocation\n(Not limited to 4KiB size)",
			"baseline": 60,
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "Allows for dynamic allocation\n(Not limited to 4KiB size)"
		},
		{
			"type": "arrow",
			"version": 26,
			"versionNonce": 370829159,
			"isDeleted": false,
			"id": "xLlMKco5WQWxjmlaqm3es",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 467.72514034047674,
			"y": 46.22430380588918,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 260.05535658921116,
			"height": 95.53052833755675,
			"seed": 521364271,
			"groupIds": [],
			"strokeSharpness": "round",
			"boundElements": [],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "x-q6ZlmruFaIlK-cEGRdg",
				"focus": 0.002228832930470572,
				"gap": 3.8597604306011135
			},
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-260.05535658921116,
					95.53052833755675
				]
			]
		},
		{
			"type": "rectangle",
			"version": 63,
			"versionNonce": 1018128009,
			"isDeleted": false,
			"id": "Be32OppMXYCcMbwio2a4K",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 5.029180751588797,
			"y": 106.05156226699259,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 187.20120790025908,
			"height": 48.73020427642865,
			"seed": 1436218543,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [],
			"updated": 1668541269892,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 73,
			"versionNonce": 893837959,
			"isDeleted": false,
			"id": "SCBBjayx0UDjviDPZoJzO",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 7.44159727890451,
			"y": 163.94885216854212,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 182.37646318988106,
			"height": 210.84261600076726,
			"seed": 1732426241,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [],
			"updated": 1668541269892,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 26,
			"versionNonce": 1358146921,
			"isDeleted": false,
			"id": "aGwbwaK7",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 207.66969540701234,
			"y": 222.37307647006702,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 147,
			"height": 35,
			"seed": 1032183023,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 1,
			"text": "Two parts",
			"rawText": "Two parts",
			"baseline": 25,
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "Two parts"
		},
		{
			"type": "text",
			"version": 11,
			"versionNonce": 729217447,
			"isDeleted": false,
			"id": "gNdjLqH5",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 22.398367722053763,
			"y": 108.99086902215697,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 95,
			"height": 35,
			"seed": 1361285327,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 1,
			"text": "Header",
			"rawText": "Header",
			"baseline": 25,
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "Header"
		},
		{
			"type": "text",
			"version": 9,
			"versionNonce": 650909769,
			"isDeleted": false,
			"id": "AZV0DdfN",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 34.94272163788719,
			"y": 186.18727028159861,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 77,
			"height": 35,
			"seed": 969445153,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 1,
			"text": "Data",
			"rawText": "Data",
			"baseline": 25,
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "Data"
		},
		{
			"type": "arrow",
			"version": 83,
			"versionNonce": 232205511,
			"isDeleted": false,
			"id": "tR8UoEoT42W0zEgK5t2hj",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 60.51405412582267,
			"y": 116.18363217189051,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 100.3552730479347,
			"height": 85.39852469084892,
			"seed": 972722639,
			"groupIds": [],
			"strokeSharpness": "round",
			"boundElements": [],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "WMsu8jA7",
				"focus": 0.31869681085381196,
				"gap": 16.76647687201438
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-100.3552730479347,
					-85.39852469084892
				]
			]
		},
		{
			"type": "text",
			"version": 119,
			"versionNonce": 1075062569,
			"isDeleted": false,
			"id": "WMsu8jA7",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -248.75399887970548,
			"y": -56.98136939097279,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 472,
			"height": 70,
			"seed": 1338909121,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [
				{
					"id": "tR8UoEoT42W0zEgK5t2hj",
					"type": "arrow"
				}
			],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 1,
			"text": "Header needs to store next heap,\nprevious heap, size",
			"rawText": "Header needs to store next heap,\nprevious heap, size",
			"baseline": 60,
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "Header needs to store next heap,\nprevious heap, size"
		},
		{
			"type": "arrow",
			"version": 18,
			"versionNonce": 402914279,
			"isDeleted": false,
			"id": "q3eW0yLiLjgDQJAY1pwFj",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 345.6236949152519,
			"y": -208.94913162048965,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 298.66658528645837,
			"height": 118.66668701171875,
			"seed": 892020393,
			"groupIds": [],
			"strokeSharpness": "round",
			"boundElements": [],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "yWowMrpD",
				"focus": 0.7107155517527654,
				"gap": 6.4649809544426375
			},
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					298.66658528645837,
					-118.66668701171875
				]
			]
		},
		{
			"type": "text",
			"version": 81,
			"versionNonce": 1463245321,
			"isDeleted": false,
			"id": "11lQtgGe",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 664.2902802017103,
			"y": -350.7824242637188,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 340,
			"height": 70,
			"seed": 151727529,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 1,
			"text": "Use of Frifgg to do this\nfor us.",
			"rawText": "Use of Frifgg to do this\nfor us.",
			"baseline": 60,
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "Use of Frifgg to do this\nfor us."
		},
		{
			"type": "text",
			"version": 144,
			"versionNonce": 1577707271,
			"isDeleted": false,
			"id": "7rfJ6nEc",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -706.1456541540545,
			"y": -599.5187940035985,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 356,
			"height": 106,
			"seed": 274285351,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"boundElements": [
				{
					"id": "B8blZ6edopem0n7OAFBUw",
					"type": "arrow"
				}
			],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"fontSize": 28,
			"fontFamily": 1,
			"text": "Load memory map given by\nbootloader\n",
			"rawText": "Load memory map given by\nbootloader\n",
			"baseline": 95,
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "Load memory map given by\nbootloader\n"
		},
		{
			"type": "arrow",
			"version": 60,
			"versionNonce": 1295069417,
			"isDeleted": false,
			"id": "B8blZ6edopem0n7OAFBUw",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -173.34597153686718,
			"y": -401.418818417661,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 163.199951171875,
			"height": 123.20001220703125,
			"seed": 2100745289,
			"groupIds": [],
			"strokeSharpness": "round",
			"boundElements": [],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "uoCEqVIf",
				"focus": -0.657927685092458,
				"gap": 6.872958127133643
			},
			"endBinding": {
				"elementId": "7rfJ6nEc",
				"focus": -0.6550536498893328,
				"gap": 13.599731445312273
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-163.199951171875,
					-123.20001220703125
				]
			]
		},
		{
			"id": "kT10PVKDY_gaN53BCJKvC",
			"type": "arrow",
			"x": -105.31458748192495,
			"y": -338.6588447182644,
			"width": 354.0000915527344,
			"height": 98.00003051757812,
			"angle": 0,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"strokeSharpness": "round",
			"seed": 2137412807,
			"version": 49,
			"versionNonce": 1046834727,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-354.0000915527344,
					98.00003051757812
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "uoCEqVIf",
				"focus": -0.04405823610923887,
				"gap": 9.887015572262953
			},
			"endBinding": {
				"elementId": "XViZK2Xj",
				"focus": -0.13353033201159084,
				"gap": 12.999923706054688
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "XViZK2Xj",
			"type": "text",
			"x": -619.314602740714,
			"y": -229.1587226479519,
			"width": 147,
			"height": 35,
			"angle": 0,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"seed": 1260562185,
			"version": 41,
			"versionNonce": 1468869577,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "kT10PVKDY_gaN53BCJKvC",
					"type": "arrow"
				},
				{
					"id": "XVxf0sqIQgl9RS5A3LpQT",
					"type": "arrow"
				}
			],
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"text": "User Mode",
			"rawText": "User Mode",
			"fontSize": 28,
			"fontFamily": 1,
			"textAlign": "left",
			"verticalAlign": "top",
			"baseline": 25,
			"containerId": null,
			"originalText": "User Mode"
		},
		{
			"id": "XVxf0sqIQgl9RS5A3LpQT",
			"type": "arrow",
			"x": -559.0734597057053,
			"y": -182.65878368310814,
			"width": 29.269687297716246,
			"height": 86.00006103515625,
			"angle": 0,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"strokeSharpness": "round",
			"seed": 1388058535,
			"version": 109,
			"versionNonce": 335745351,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-29.269687297716246,
					86.00006103515625
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "XViZK2Xj",
				"focus": 0.05029908823690966,
				"gap": 11.49993896484375
			},
			"endBinding": {
				"elementId": "AUPgYfwl",
				"focus": 0.4964264618491915,
				"gap": 15.500030517578125
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "AUPgYfwl",
			"type": "text",
			"x": -1007.3146332582921,
			"y": -81.15869213037377,
			"width": 541,
			"height": 35,
			"angle": 0,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"seed": 1755510377,
			"version": 122,
			"versionNonce": 601570695,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "XVxf0sqIQgl9RS5A3LpQT",
					"type": "arrow"
				},
				{
					"id": "OmJHA-2Xccoqn7qik2Jf9",
					"type": "arrow"
				}
			],
			"updated": 1668541273132,
			"link": null,
			"locked": false,
			"text": "Only allocate a couple pages if needed",
			"rawText": "Only allocate a couple pages if needed",
			"fontSize": 28,
			"fontFamily": 1,
			"textAlign": "left",
			"verticalAlign": "top",
			"baseline": 25,
			"containerId": null,
			"originalText": "Only allocate a couple pages if needed"
		},
		{
			"id": "OmJHA-2Xccoqn7qik2Jf9",
			"type": "arrow",
			"x": -693.3146942934484,
			"y": -34.658753165530015,
			"width": 18.000030517578125,
			"height": 181.99996948242188,
			"angle": 0,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"strokeSharpness": "round",
			"seed": 2053737865,
			"version": 60,
			"versionNonce": 803946921,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1668541312273,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					18.000030517578125,
					181.99996948242188
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "AUPgYfwl",
				"focus": -0.14925501413037945,
				"gap": 11.49993896484375
			},
			"endBinding": {
				"elementId": "Sj2JaFBD",
				"focus": -0.10427318980611523,
				"gap": 7.5
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "Sj2JaFBD",
			"type": "text",
			"x": -919.314602740714,
			"y": 154.84121631689186,
			"width": 555,
			"height": 70,
			"angle": 0,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"strokeSharpness": "sharp",
			"seed": 145130089,
			"version": 205,
			"versionNonce": 1804300935,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "OmJHA-2Xccoqn7qik2Jf9",
					"type": "arrow"
				}
			],
			"updated": 1668541309540,
			"link": null,
			"locked": false,
			"text": "Then when needed (Page Fualt)\ngive a page and returnt to the process",
			"rawText": "Then when needed (Page Fualt)\ngive a page and returnt to the process",
			"fontSize": 28,
			"fontFamily": 1,
			"textAlign": "left",
			"verticalAlign": "top",
			"baseline": 60,
			"containerId": null,
			"originalText": "Then when needed (Page Fualt)\ngive a page and returnt to the process"
		},
		{
			"id": "_2yOKzjgCNKhqOzV8xvZF",
			"type": "freedraw",
			"x": -685.3145111879796,
			"y": -32.65878368310814,
			"width": 2.0001220703125,
			"height": 153.99993896484375,
			"angle": 0,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"strokeSharpness": "round",
			"seed": 1114432329,
			"version": 31,
			"versionNonce": 675237991,
			"isDeleted": true,
			"boundElements": null,
			"updated": 1668541269892,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					0,
					8.000030517578125
				],
				[
					0,
					15.999908447265625
				],
				[
					-2.0001220703125,
					23.99993896484375
				],
				[
					-2.0001220703125,
					31.999969482421875
				],
				[
					-2.0001220703125,
					40
				],
				[
					-2.0001220703125,
					43.99993896484375
				],
				[
					-2.0001220703125,
					50
				],
				[
					-2.0001220703125,
					51.999969482421875
				],
				[
					-2.0001220703125,
					55.999908447265625
				],
				[
					-2.0001220703125,
					60
				],
				[
					-2.0001220703125,
					63.99993896484375
				],
				[
					-2.0001220703125,
					68.00003051757812
				],
				[
					-2.0001220703125,
					70
				],
				[
					-2.0001220703125,
					73.99993896484375
				],
				[
					-2.0001220703125,
					80
				],
				[
					-2.0001220703125,
					83.99993896484375
				],
				[
					-2.0001220703125,
					90
				],
				[
					-2.0001220703125,
					98.00003051757812
				],
				[
					-2.0001220703125,
					103.99993896484375
				],
				[
					-2.0001220703125,
					111.99996948242188
				],
				[
					-2.0001220703125,
					120
				],
				[
					-2.0001220703125,
					131.99996948242188
				],
				[
					-2.0001220703125,
					141.99996948242188
				],
				[
					-2.0001220703125,
					143.99993896484375
				],
				[
					-2.0001220703125,
					148.00003051757812
				],
				[
					-2.0001220703125,
					151.99996948242188
				],
				[
					-2.0001220703125,
					153.99993896484375
				],
				[
					-2.0001220703125,
					153.99993896484375
				]
			],
			"pressures": [],
			"simulatePressure": true,
			"lastCommittedPoint": [
				-2.0001220703125,
				153.99993896484375
			]
		}
	],
	"appState": {
		"theme": "dark",
		"viewBackgroundColor": "#ffffff",
		"currentItemStrokeColor": "#000000",
		"currentItemBackgroundColor": "transparent",
		"currentItemFillStyle": "hachure",
		"currentItemStrokeWidth": 1,
		"currentItemStrokeStyle": "solid",
		"currentItemRoughness": 1,
		"currentItemOpacity": 100,
		"currentItemFontFamily": 1,
		"currentItemFontSize": 28,
		"currentItemTextAlign": "left",
		"currentItemStrokeSharpness": "sharp",
		"currentItemStartArrowhead": null,
		"currentItemEndArrowhead": "arrow",
		"currentItemLinearStrokeSharpness": "round",
		"gridSize": null,
		"colorPalette": {}
	},
	"files": {}
}
```
%%