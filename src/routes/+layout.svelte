<script lang="ts">
	import Toc from '$lib/components/Toc.svelte';
	import RightPanel from '$lib/components/rightpanel.svelte';
	import { Grid, Row, Column } from 'carbon-components-svelte';
	import "carbon-components-svelte/css/all.css";
	const currentYear = new Date().getFullYear();
  import Icon from "@iconify/svelte";
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
          <a href="https://github.com/Talha-Ijaz-Qureshi/linux-guide"><h2>View Source Code</h2></a>

          <div class="logo">
            <Icon icon="carbon:shuffle" width="530" height="530"  style="color: #78a9ff" />
          </div>
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
            <Icon icon="carbon:linux" width="32" height="32"  style="color: #78a9ff" />            
            <Icon icon="carbon:earth-filled" width="32" height="32"  style="color: #78a9ff" />        
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