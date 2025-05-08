<script lang="ts">
	// ===================================================================
	// MAIN APPLICATION COMPONENT
	// Configures and integrates scrollyteller with visualizations
	// ===================================================================
	import Scrollyteller, { loadScrollyteller } from '$lib/index.js';
	import VegaChart from './VegaChart.svelte';
	import { onMount } from 'svelte';

	// Import chart specifications from JSON files
	import chart01 from './Charts/chart_01.json';
	import chart03 from './Charts/chart_03.json';
	import chart04 from './Charts/chart_04.json';
	import chart06 from './Charts/chart_06.json';
	import chart07 from './Charts/chart_07.json';
	
	// ===================================================================
	// SCROLLYTELLER CONFIGURATION
	// Initialize scrollyteller with configuration parameters
	// ===================================================================
	const scrollyData = loadScrollyteller(
		'test', // Scrollyteller name - corresponds to #scrollytellerNAMEtest in CoreMedia
		'u-full', // Class for mount point - u-full makes it full width in Odyssey
		'mark' // Marker prefix - #markNUMBER1 etc. in CoreMedia
	);

	// App state
	let number = 0; // Current section number
	let stProgress; // Scrollyteller progress data
	let currentSpec = null; // Current chart specification

	// ===================================================================
	// CHART METADATA
	// Content information for each visualization section
	// ===================================================================
	const chartInfo = [
		{
			title: "The Beginning",
			description: "Our journey begins with the foundations that will shape our future. These are the building blocks of what comes next, setting the stage for a revolutionary transformation in how we live and work.",
			alignment: "left"
		},
		{
			title: "Digital Revolution",
			description: "The acceleration of technology creates new opportunities and challenges. What seemed impossible yesterday becomes standard today.",
			alignment: "center"
		},
		{
			title: "Global Connectivity",
			description: "As borders blur in the digital realm, communities form across continents, reshaping how we communicate and collaborate.",
			alignment: "right"
		},
		{
			title: "AI Renaissance",
			description: "Artificial intelligence evolves from simple automation to creative partnership, augmenting human capabilities in ways previously unimagined and opening new frontiers for innovation.",
			alignment: "left"
		},
		{
			title: "Sustainability Shift",
			description: "The urgent need for environmental harmony drives technological development toward sustainable solutions, creating a new paradigm for progress that respects planetary boundaries.",
			alignment: "center"
		},
		{
			title: "New Horizons",
			description: "Exploration beyond our planet becomes increasingly viable, opening up possibilities for humanity's expansion into the cosmos.",
			alignment: "right"
		},
		{
			title: "Convergence",
			description: "The integration of biological, digital, and physical realms creates entirely new categories of experience and capability, fundamentally transforming what it means to be human in the coming century.",
			alignment: "center"
		}
	];

	// ===================================================================
	// EVENT HANDLERS
	// Handle scrollyteller events for markers and progress
	// ===================================================================
	
	// Handle marker changes (when user scrolls to a new section)
	const onMarker = (marker) => {
		number = marker.number;
		updateVisualization(number);
	};

	// Track scrolling progress for animations
	const onProgress = (progress) => {
		stProgress = progress;
	};

	// ===================================================================
	// VISUALIZATION MANAGEMENT
	// Update displayed content based on current section
	// ===================================================================
	
	// Update the visualization based on the current marker number
	function updateVisualization(markerNumber) {
		// Select the appropriate chart specification for each section
		switch (markerNumber) {
			case 1:
				currentSpec = chart01; // Chart visualization
				break;
			case 2:
				currentSpec = null; // Full-screen image instead of chart
				break;
			case 3:
				currentSpec = chart03; // Chart visualization
				break;
			case 4:
				currentSpec = chart04; // Chart visualization
				break;
			case 5:
				currentSpec = null; // Full-screen image instead of chart
				break;
			case 6:
				currentSpec = chart06; // Chart visualization
				break;
			case 7:
				currentSpec = chart07; // Chart visualization
				break;
			default:
				currentSpec = null;
				break;
		}
	}

	// Initialize with first visualization on component mount
	onMount(() => {
		updateVisualization(1);
	});
</script>

<svelte:head>
	<!-- 
	// ===================================================================
	// FONT IMPORTS
	// Typography resources for the application
	// ===================================================================
	-->
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
	<link href="https://fonts.googleapis.com/css2?family=Nunito:ital,wght@0,200..1000;1,200..1000&display=swap" rel="stylesheet">
</svelte:head>

<!-- 
// ===================================================================
// HEADER SECTION
// Full-screen hero image with title overlay
// ===================================================================
-->
<div class="fullscreen-chapter header-image">
	<div class="header-overlay"></div>
	<div class="header-content">
		<h1 class="main-title">Timeline to the Future</h1>
		<h2 class="sub-title">Martina and Rosario</h2>
	</div>
</div>

<!-- 
// ===================================================================
// INTRODUCTION CONTENT
// Opening paragraphs before scrollytelling sections
// ===================================================================
-->
<div class="content-container">
	<p class="content-paragraph">The future arrives gradually, then suddenly. Technology that once seemed like science fiction becomes commonplace, reshaping our expectations and daily lives. This exploration takes us through the key developments that are building our future, from the incremental advances happening today to the revolutionary transformations on the horizon.</p>
	<p class="content-paragraph">How do we navigate this accelerating pace of change? What opportunities and challenges await us? And most importantly, how can we shape these technologies to create the future we want to inhabit? Join us as we traverse the timeline to our collective future.</p>
	<div class="image-left">
		<img src="../../src/TestExample/Images/placeholder.png" alt="Technology concept" />
	</div>
	<p class="content-paragraph">The convergence of artificial intelligence, biotechnology, renewable energy, and digital connectivity is creating unprecedented potential for human advancement. But realizing this potential requires thoughtful consideration of how these technologies intersect with our values, institutions, and communities.</p>
	<p class="content-paragraph">This visual journey explores both the technical breakthroughs and the social adaptations that will define our path forward. By understanding these dynamics, we can better participate in shaping a future that amplifies human creativity, sustainability, and equity rather than undermining these core values.</p>
</div>

<!-- 
// ===================================================================
// CHAPTER SECTION - BLACK
// Full-screen black background section with white text
// ===================================================================
-->
<div class="fullscreen-chapter black-bg">
	<div class="content-container">
		<h2>The Elements of Change</h2>
		<p class="content-paragraph">Progress doesn't happen in isolation. The most significant breakthroughs emerge from the interaction of multiple disciplines, technologies, and social factors. Understanding these interconnections helps us anticipate how current developments might evolve into future transformations.</p>
		<p class="content-paragraph">Four key elements are shaping our trajectory: computational power that continues to advance exponentially; connectivity that dissolves traditional boundaries between people and organizations; intelligence systems that augment human capabilities; and sustainability imperatives that redirect technological development toward preserving our planetary home.</p>
		<p class="content-paragraph">Each visualization in this exploration represents a different dimension of this complex evolutionary process. Together, they offer a glimpse into not just what might happen, but how and why these changes will transform our world.</p>
	</div>
</div>

<!-- 
// ===================================================================
// DATAWRAPPER IFRAME - BROWSER TRENDS
// Interactive visualization showing browser market share changes
// ===================================================================
-->
<div class="content-container">
	<h2>The Evolution of Digital Tools</h2>
	<p class="content-paragraph">The rise of Google Chrome illustrates how quickly digital landscapes can transform when innovative approaches meet user needs. This pattern of rapid adoption reflects broader trends in how technologies establish new standards and reshape industries.</p>
	<div class="datawrapper-container">
		<iframe title="The rise of Google Chrome" aria-label="Interactive line chart" id="datawrapper-chart-Beu4R" src="https://datawrapper.dwcdn.net/Beu4R/1/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="421" data-external="1"></iframe>
		<script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r,i=0;r=e[i];i++)if(r.contentWindow===a.source){var d=a.data["datawrapper-height"][t]+"px";r.style.height=d}}}))}();
		</script>
	</div>
	<p class="content-paragraph">Market disruptions like this demonstrate how user preferences can rapidly consolidate around superior experiences. The ability to anticipate and adapt to these transitions is becoming a critical skill for organizations and individuals in our accelerating technological environment.</p>
</div>

<!-- 
// ===================================================================
// MAP VISUALIZATION
// Embedded Datawrapper map visualization
// ===================================================================
-->
<div style="min-height:730px" id="datawrapper-vis-V8sUH"><script type="text/javascript" defer src="https://datawrapper.dwcdn.net/V8sUH/embed.js" charset="utf-8" data-target="#datawrapper-vis-V8sUH"></script><noscript><img src="https://datawrapper.dwcdn.net/V8sUH/full.png" alt="" /></noscript></div>

<div class="content-container">
	<p class="content-paragraph">The global distribution of innovation hubs is shifting. While traditional centers like Silicon Valley remain important, new ecosystems are emerging across the globe, each with distinctive specializations and approaches. This geographical diversification enriches the innovation landscape and accelerates cross-pollination of ideas.</p>
	<p class="content-paragraph">Local contexts shape how technologies develop and deploy. Cultural values, regulatory environments, and economic conditions all influence which solutions gain traction in different regions. This diversity creates a natural laboratory for different approaches, allowing multiple paths toward the future to be explored simultaneously.</p>
	<div style="min-height:430px" id="datawrapper-vis-FkN5a"><script type="text/javascript" defer src="https://datawrapper.dwcdn.net/FkN5a/embed.js" charset="utf-8" data-target="#datawrapper-vis-FkN5a"></script><noscript><img src="https://datawrapper.dwcdn.net/FkN5a/full.png" alt="" /></noscript></div>
	<p></p>
	<p class="content-paragraph">Investment patterns reveal shifting priorities across sectors. Capital flows increasingly toward technologies that address pressing global challenges, from climate adaptation to healthcare access. This reorientation of resources accelerates progress in these critical domains while potentially slowing development in others.</p>
	<p class="content-paragraph">The timeline to impact varies widely across technologies. Some innovations, particularly in software and digital services, can scale rapidly across the globe in months. Others, especially those requiring physical infrastructure or regulatory approval, may take decades to reach their full potential. Understanding these different timescales helps set realistic expectations for change.</p>
</div>

<!-- 
// ===================================================================
// SCROLLYTELLER COMPONENT
// Main scrollytelling section with data visualizations
// ===================================================================
-->
<Scrollyteller
	panels={scrollyData.panels}
	{onMarker}
	{onProgress}
>
	<div class="graphic">
		<div class="chart-container">
			<!-- Render different content based on current section -->
			{#if number === 1}
				<!-- Section 1: Chart with left alignment -->
				<VegaChart 
					spec={chart01}
					alignment={chartInfo[0].alignment} 
				/>
				
				<div class="chart-info align-left">
					<h3 class="chart-title">{chartInfo[0].title}</h3>
					<p class="chart-description">{chartInfo[0].description}</p>
				</div>
			
			{:else if number === 2}
				<!-- Section 2: Full-screen image -->
				<div class="fullscreen-image-container">
					<img src="../src/TestExample/Images/placehold-19201080-orange.png" alt="Digital revolution visualization" class="fullscreen-image" />
				</div>
			
			{:else if number === 3}
				<!-- Section 3: Chart with right alignment -->
				<VegaChart 
					spec={chart03}
					alignment={chartInfo[2].alignment} 
				/>
				
				<div class="chart-info align-right">
					<h3 class="chart-title">{chartInfo[2].title}</h3>
					<p class="chart-description">{chartInfo[2].description}</p>
				</div>
			
			{:else if number === 4}
				<!-- Section 4: Chart with left alignment -->
				<VegaChart 
					spec={chart04}
					alignment={chartInfo[3].alignment} 
				/>
				
				<div class="chart-info align-left">
					<h3 class="chart-title">{chartInfo[3].title}</h3>
					<p class="chart-description">{chartInfo[3].description}</p>
				</div>
			
			{:else if number === 5}
				<!-- Section 5: Full-screen image -->
				<div class="fullscreen-image-container">
					<img src="../src/TestExample/Images/placehold-19201080-blue.png" alt="Sustainability visualization" class="fullscreen-image" />
				</div>
			
			{:else if number === 6}
				<!-- Section 6: Chart with right alignment -->
				<VegaChart 
					spec={chart06}
					alignment={chartInfo[5].alignment} 
				/>
				
				<div class="chart-info align-right">
					<h3 class="chart-title">{chartInfo[5].title}</h3>
					<p class="chart-description">{chartInfo[5].description}</p>
				</div>
			
			{:else if number === 7}
				<!-- Section 7: Chart with center alignment -->
				<VegaChart 
					spec={chart07}
					alignment={chartInfo[6].alignment} 
				/>
				
				<div class="chart-info align-center">
					<h3 class="chart-title">{chartInfo[6].title}</h3>
					<p class="chart-description">{chartInfo[6].description}</p>
				</div>
			
			{:else}
				<!-- Default/Initial state before scrolling begins -->
				<div class="initial-state">
					<p>Scroll to begin the journey</p>
				</div>
			{/if}
		</div>
	</div>
</Scrollyteller>

<!-- 
// ===================================================================
// CONTENT SECTION
// Additional content after scrollytelling experience
// ===================================================================
-->
<div class="content-container">
	<p class="content-paragraph">The convergence of these technological streams will reshape what it means to be human in the 21st century. Boundaries between physical and digital realms will continue to blur, creating hybrid experiences that combine the best of both worlds. Our relationship with machines will become more symbiotic as AI systems become more capable of understanding context and collaborating effectively.</p>
	<p class="content-paragraph">Adaptation will be essential. Education systems will need to evolve to prepare people for careers that don't yet exist. Organizations must become more agile to seize fleeting opportunities in rapidly changing markets. And individuals will need to cultivate both technical literacy and humanistic wisdom to navigate this increasingly complex landscape.</p>
	<p class="content-paragraph">The democratization of powerful technologies creates both opportunities and risks. As tools that were once restricted to specialized institutions become accessible to small teams and individuals, innovation can accelerate and diversify. However, this same dynamic makes governance more challenging, requiring new approaches to managing technologies with significant societal implications.</p>
	<p class="content-paragraph">Despite these challenges, there is reason for optimism. Human ingenuity has consistently found ways to channel technological change toward positive outcomes. By maintaining focus on core values like human dignity, environmental stewardship, and inclusive prosperity, we can shape these powerful tools to create a future that expands rather than diminishes human flourishing.</p>
</div>

<!-- 
// ===================================================================
// BEIGE CHAPTER SECTION
// Full-screen beige background section with contrast text
// ===================================================================
-->
<div class="fullscreen-chapter beige-bg">
	<div class="content-container">
		<h2>Pathways Forward</h2>
		<p class="content-paragraph">The path to our technological future isn't predetermined. It will be shaped by countless decisions made by individuals, organizations, and societies. By understanding the dynamics at play, we can make more informed choices that align technological development with human wellbeing and environmental sustainability.</p>
		<p class="content-paragraph">Engagement is crucial. The future belongs to those who participate in creating it. Whether through technological development, policy advocacy, artistic expression, or ethical discourse, each contribution helps steer our collective journey toward a future we want to inhabit.</p>
	</div>
</div>

<div class="content-container">
	<p class="content-paragraph">Innovation increasingly happens at the intersection of disciplines. The most transformative developments often emerge when expertise from different domains combines in novel ways. This cross-pollination of ideas accelerates breakthrough solutions to complex challenges.</p>
	<p class="content-paragraph">Distributed collaboration enables global problem-solving at unprecedented scale. Digital platforms allow diverse participants to contribute regardless of location, creating powerful collective intelligence. These networked approaches are particularly effective for addressing multifaceted global challenges.</p>
	<div style="min-height:591px" id="datawrapper-vis-bbmLi"><script type="text/javascript" defer src="https://datawrapper.dwcdn.net/bbmLi/embed.js" charset="utf-8" data-target="#datawrapper-vis-bbmLi"></script><noscript><img src="https://datawrapper.dwcdn.net/bbmLi/full.png" alt="" /></noscript></div>	<p></p>
	<p class="content-paragraph">Long-term thinking becomes increasingly valuable in a world of accelerating change. By considering multiple time horizons simultaneously, we can better navigate immediate challenges while steering toward desirable futures. This balanced perspective helps avoid short-term solutions that create larger problems down the road.</p>
	<p class="content-paragraph">The most profound innovations often transform not just what we can do, but how we understand ourselves and our world. As we develop increasingly sophisticated tools, we simultaneously evolve new frameworks for making sense of our changing reality. This co-evolution of technology and meaning will define the coming decades.</p>
</div>

<!-- 
// ===================================================================
// FOOTER SECTION
// Site footer with contact links and additional information
// ===================================================================
-->
<footer class="site-footer">
	<div class="footer-container">
		<div class="footer-content">
			<h3 class="footer-heading">Timeline to the Future</h3>
			<p class="footer-text">A visual exploration of technological evolution and its impact on society.</p>
			<p class="footer-text">Created by Martina and Rosario, May 2025</p>
			<p class="footer-text">Contact: future@timelineproject.org</p>
		</div>
		<div class="footer-links">
			<p class="footer-text">This project is an adaptation of the <a href="https://github.com/abcnews/scrollyteller">Scrollyteller</a> by ABC News.</p>
		</div>
	</div>
</footer>