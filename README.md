# Less Oldie Compiler

Less Oldie Compiler is a simple, mobile-first solition that reducees time and effort by extracting breakpoint specific styles into less mixins. By doing this Less allows these mixins to be defined at the specified breakpoints and reused for our IE7/8 specific styling. This allows the developer to write less while still keeping his/her styles responsive. 

## Step1: Mobile
Write all mobile styling first outside of all breakpoints at the top of your file:

    /* 
    --------------------------
    Mobile Styles
    (Write all your mobile styles here)
    --------------------------
    */
    .test {
	    background-color:yellow;
    }

## Step 2: Setup your 768 Breakpoint
Write all tablet-sized styling inside the designated sevensixtyeight mixin:

	/* 
	--------------------------
	768 Breakpoint
	(Write all 768 breakpoint styles here)
	--------------------------
	*/
	.sevensixtyeight() {
		.test {
			background-color:blue;
			color:red;
			margin-top:20px;
		}
	}

## Step 3: Setup your 960 Breakpoint
Write all desktop-sized styling inside the designated ninesixty mixin:

	/* 
	--------------------------
	968 Breakpoint
	(Write all 968 breakpoint styles here)
	--------------------------
	*/
	.ninesixty() {
		.test {
			background-color:green;
			position: absolute;
		}
	}

## Step 4: Go get a beer
...because all your styling will be imported into the actual media queries as well as your .oldie styles at the bottom of your file. Simple as that.

	/* 
	--------------------------
	Compiler
	(Do not write breakpoint specific styles)
	--------------------------
	*/
	@media(min-width:768px) {
		.sevensixtyeight();
	} @media(min-width:960px) {
		.ninesixty();
	} .oldie {
		.sevensixtyeight();
		.ninesixty();
	}