# Oldie Compiler

Oldie Compiler is a simple, mobile-first solution that reduces time and effort by extracting breakpoint specific styles into Less/Sass mixins. This allows the mixins to be defined at any specified breakpoint and reused for IE7/8 specific styling. This allows the developer to write less while still keeping his/her styles responsive. 

## Step1: Mobile
Write all global styling as you normally would outside of all breakpoints at the top of your file. As a good practice scope them to the body class to avoid any style-specific scoping issues.

    /* 
    --------------------------
    Global Styles
    (scoped to the body class)
    --------------------------
    */
    body.your-body-class {
	    
    }

## Step 2: Setup 480 Breakpoint (optional)

    /* 
    --------------------------
    Mobile Specific Styles 
    --------------------------
    */
    .foureighty() {
    	body.your-body-class {
	    
    	}
    }

## Step 3: Setup your 768 Breakpoint
Write all tablet-sized styling inside the sevensixtyeight mixin:

	/* 
	--------------------------
	768 Breakpoint
	--------------------------
	*/
	.sevensixtyeight() {
		body.your-body-class {
			
		}
	}

## Step 4: Setup your 960 Breakpoint
Write all desktop-sized styling inside the ninesixty mixin:

	/* 
	--------------------------
	968 Breakpoint
	--------------------------
	*/
	.ninesixty() {
		.test {
			background-color:green;
			position: absolute;
		}
	}

## Step 4: Setup 1280 Breakpoint (optional)
Write all 1280 wide specific styles inside the tweleveeighty mixin:

	/* 
	--------------------------
	1280 Breakpoint
	--------------------------
	*/
	.tweleveeighty() {
		body.your-body-class {

		}
	}

## Step 5: Setup 1920 Breakpoint (optional)
Write all HD 1920 wide specific styles inside the tweleveeighty mixin:

	/* 
	--------------------------
	1920 Breakpoint
	--------------------------
	*/
	.nineteentwenty() {
		body.your-body-class {

		}
	}

## Step 6: Setup Retina Styles (optional only if you're a shmuck)
All 2x high rez image styling can be lest in the retina mixin:

	/* 
	--------------------------
	Retina 
	(Write all retina specific image styling here)
	--------------------------
	*/
	.retina() {
		body.your-body-class {
			
		}
	}

## Step 6: Go get a beer
...because all your styling will be imported into the actual media queries as well as your .oldie styles at the bottom of your file. Simple as that.

	/* 
	--------------------------
	Compiler
	(Do not write breakpoint specific styles here)
	--------------------------
	*/
	@media (min-width:480px) {
		.foureighty();
	} @media(min-width:768px) {
		.sevensixtyeight();
	} @media(min-width:960px) {
		.ninesixty();
	} @media(min-width:1280px) {
		.tweleveeighty();
	} @media(min-width:1920) {
		.nineteentwenty();
	} @media (-webkit-min-device-pixel-ratio : 1.5),
	(min-device-pixel-ratio : 1.5) {
		.retina();
	} .oldie {
		.sevensixtyeight();
		.ninesixty();
	}

The result? All of the media queries you wrote plus auto-compiled IE styling. 

	body.your-body-class #main {
	  width:100%;
	}
	@media (min-width: 768px) {
	  body.your-body-class #main {
	    padding:0 20x;
	    width:748px;
	  }
	}
	@media (min-width: 960px) {
	  body.your-body-class #main {
	    width:920px;
	  }
	}
	@media (min-width: 1260px) {
		body.your-body-class #main {
			width:1220px;
		}
	}
	@media (min-width: 1920px) {
		body.your-body-class #main {
			width:1880px;
		}
	}
	@media (-webkit-min-device-pixel-ratio : 1.5),
	(min-device-pixel-ratio : 1.5) {
		body.your-body-class #main #logo {
			background: url('../images/@2x-rez-logo.png') top left no-repeat transparent;
			background-size:400px 400px;
		}
	}
	.oldie body.your-body-class #main {
		padding:0 20x;
	    width:748px;
	}
	.oldie body.your-body-class #main {
	  width:920px;
	}

## Both Less and Sass templates available:
* [Less Template](https://github.com/seawolff/oldiecompiler/blob/master/less-template.less)
* [Sass Template](https://github.com/seawolff/oldiecompiler/blob/master/sass-template.sass)