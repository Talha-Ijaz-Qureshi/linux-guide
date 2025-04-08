<script lang="ts">
	import Toc from '$lib/components/Toc.svelte';
	import RightPanel from '$lib/components/rightpanel.svelte';
	import { Grid, Row, Column } from 'carbon-components-svelte';
	import "carbon-components-svelte/css/all.css";
	import { Link } from "carbon-components-svelte";
	const currentYear = new Date().getFullYear();
  </script>
<svelte:head>
  <title>Linux Migration Compass</title>
  <meta name="viewport" content="height=device-height, 
                      width=device-width, initial-scale=1.0, 
                      minimum-scale=1.0, maximum-scale=1.0, 
                      user-scalable=no, target-densitydpi=device-dpi">
</svelte:head>

  <Grid>
	<Row>
	  <Column sm={4} md={2} lg={4}>
		<Toc />
	  </Column>
	  <Column sm={8} md={8} lg={8}>
		<slot />
<footer class="footer">
	<div class="footer-content">
    <h1>Linux Migration Compass</h1>
	  <h2>Copyleft - {currentYear} Linux Migration Compass - Talha Ijaz</h2>
    <a href="/"><h2>View Source Code</h2></a>

    <svg xmlns="http://www.w3.org/2000/svg" width="530" height="530" class="logo" viewBox="0 0 32 32">
      <path fill="#78a9ff" d="M22.59 19.41L26.17 23h-6.62l-4.37-7l4.37-7h6.62l-3.58 3.59L24 14l6-6l-6-6l-1.41 1.41L26.17 7h-6.62a2 2 0 0 0-1.69.94L14 14.11l-3.86-6.17A2 2 0 0 0 8.45 7H2v2h6.45l4.37 7l-4.37 7H2v2h6.45a2 2 0 0 0 1.69-.94L14 17.89l3.86 6.17a2 2 0 0 0 1.69.94h6.62l-3.58 3.59L24 30l6-6l-6-6Z"></path>
    </svg>
    <div class="lic">
      <h3>
        License Rationale - GNU General Public License v3.0 
      </h3>
      <p>
        This work is licensed under the GNU General Public License v3.0. You may copy, distribute and modify this work under the terms of the GNU GPL version 3 or any later version.
      </p>
      <p>
        This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
      </p>
      <p>
        For more information, see: <a href="https://www.gnu.org/licenses/gpl-3.0.en.html">https://www.gnu.org/licenses/gpl-3.0.en.html</a>
      </p>
    </div>
    
    <div class="speshal">
      <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 32 32"><path fill="#78a9ff" d="m29.895 23.542l-1.724-3.447a2 2 0 0 0-1.789-1.106h-.468a14.9 14.9 0 0 0-1.82-4.597C23.065 12.442 22 10.428 22 8a6 6 0 0 0-12 0a13 13 0 0 1-2.049 6.215a14.7 14.7 0 0 0-1.87 4.776h-.463a2 2 0 0 0-1.789 1.106l-1.723 3.447a1 1 0 0 0 .097 1.05l4.029 5.326a3 3 0 0 0 3.848.652l1.874-1.124A13.8 13.8 0 0 0 16 30a13.8 13.8 0 0 0 4.049-.553l1.871 1.123a3 3 0 0 0 1.539.43a3.04 3.04 0 0 0 2.338-1.119l4-5.288a1 1 0 0 0 .098-1.051m-7.569-8.216a14.8 14.8 0 0 1 1.56 3.663h-2.148a16.7 16.7 0 0 0-.98-2.645a12.7 12.7 0 0 1-.879-2.446a9 9 0 0 0 1.003-1.427l.039-.072a31 31 0 0 0 1.405 2.927M12 21a9.4 9.4 0 0 1 1.073-3.852c.256-.582.516-1.175.726-1.799a4.05 4.05 0 0 0 4.402 0c.21.624.47 1.217.726 1.8A9.4 9.4 0 0 1 20 21c0 1.288-.415 3-4 3s-4-1.712-4-3m6.51-8.575A3.63 3.63 0 0 1 16 14a3.63 3.63 0 0 1-2.51-1.576a7.64 7.64 0 0 1 5.02 0ZM12 8a4 4 0 0 1 8 0a11 11 0 0 0 .467 3.115a8 8 0 0 0-1.467-.63V8h-2v2.054a9.3 9.3 0 0 0-2 0V8h-2v2.485a8 8 0 0 0-1.478.637A10.7 10.7 0 0 0 12 8m-2.285 7.16a30 30 0 0 0 1.354-2.78l.049.09a9 9 0 0 0 1.003 1.428a12.7 12.7 0 0 1-.879 2.445a16.7 16.7 0 0 0-.98 2.648H8.104a14 14 0 0 1 1.61-3.832m1.37 12.477l-2.034 1.22a.99.99 0 0 1-1.253-.18l-3.626-4.794l1.446-2.892h3.706l2.166 5.394a1.004 1.004 0 0 1-.405 1.252m2.316.117a2.96 2.96 0 0 0-.056-2.11A9 9 0 0 0 16 26a9 9 0 0 0 2.656-.356a3 3 0 0 0-.054 2.11a13.9 13.9 0 0 1-5.2 0Zm10.83.884a.996.996 0 0 1-1.282.217l-2.034-1.22a1.01 1.01 0 0 1-.396-1.273l2.157-5.373h3.705l1.446 2.892Z"/></svg>
      <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 32 32"><path fill="#78a9ff" d="M16 2a14 14 0 1 0 14 14A14.016 14.016 0 0 0 16 2M4.02 16.394l1.338.446L7 19.303v1.283a1 1 0 0 0 .293.707L10 24v2.377a12 12 0 0 1-5.98-9.983M16 28a12 12 0 0 1-2.572-.285L14 26l1.805-4.512a1 1 0 0 0-.097-.926l-1.411-2.117a1 1 0 0 0-.832-.445h-4.93l-1.248-1.873L9.414 14H11v2h2v-2.734l3.868-6.77l-1.736-.992L14.277 7h-2.742L10.45 5.371A11.86 11.86 0 0 1 20 4.7V8a1 1 0 0 0 1 1h1.465a1 1 0 0 0 .832-.445l.877-1.316A12 12 0 0 1 26.894 11H22.82a1 1 0 0 0-.98.804l-.723 4.47a1 1 0 0 0 .54 1.055L25 19l.685 4.056A11.98 11.98 0 0 1 16 28"/></svg>
  
    </div>    
  </div>
  </footer>
	  </Column>
	  <Column sm={4} md={2} lg={2}>
		<RightPanel />
	  </Column>
	</Row>
  </Grid>

  <style>
	
	:global(.bx--grid) {
	  max-width: 100%;
	  padding: 2rem;
	}
  .logo {
    position: absolute;
    z-index: 0;
    right: -2em;
    opacity: .2;
    top: -2em;
  }
  h1 {
	  font-size: 5rem;
	  color: #78a9ff;
	  font-family: 'IBM Plex Serif', serif;
	  font-weight: 900;
	  opacity: 1;
    z-index: 1;
    line-height: .9;
    margin-bottom: .5rem;
	}
	h2 {
	  font-size: 1rem;
	  color: #78a9ff;
	  font-family: 'IBM Plex Serif', serif;
	  font-weight: 900;
	  opacity: .9;
    z-index: 1;
	}
  h3 {
    font-family: 'IBM Plex Serif', serif;
    font-weight: 400;
    margin: .5em 0;
    color: #c6c6c6;
  }
	.footer {
    background-color: var(--cds-layer);
    color: var(--cds-text-primary);
    padding: 1rem 2rem;
    padding-top: 1.2rem;
    margin-top: 10vh;
    border-top: 1px solid var(--cds-border-subtle);
    font-size: 0.875rem;
    height: fit-content;
    position: relative;
    overflow: hidden;
    border-radius: 1px;

  }
  .lic {
    background-color: #2e3b44;
    padding: 1rem;
    padding-top: 1rem;
    padding-top: 0;
    border-radius: 1px;
    margin-top: 2rem;
    z-index: 1;
    width: 100%;
    font-family: 'IBM Plex Serif', serif;
    border-bottom: 1px solid #393939;
    margin-bottom: 1rem;

  }
  .lic p {
    font-size: 1.1rem;
    line-height: 1.7;
    margin: .5em 0;
    color: #c6c6c6;
  }
  .footer-content {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    align-items: flex-start;
    justify-content: center;
  }


  .footer a {
    color: var(--cds-link-primary);
  }

  .footer a:hover {
    text-decoration: underline;
  }

  @media (max-width: 1199px) {
		h1 {
			font-size: 3rem;
      margin-left: 1rem;
		}
		h2 {
			font-size: 1rem;
      margin-left: 1rem;

		}
		h3 {
			font-size: 1.5rem;
		}
		p {
			font-size: 0.75rem;
			line-height: 1.7;
		}

    .footer {
      padding: 1.2rem 0;
    }

    .speshal {
      margin-left: 1rem;
    }
	}

  </style>