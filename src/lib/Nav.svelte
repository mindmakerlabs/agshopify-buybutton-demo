<!-- src/lib/Nav.svelte -->
<script>
    import { onMount } from 'svelte';
  
    const pages = [
      { title: 'Overview', route: '/' },
      { title: 'Filter Products', route: '/filter-products' },
      { title: 'Case Studies', route: '/case-studies' },
      { title: 'FAQ', route: '/faq' },
    ];
  
    let currentPath = '';
    let queryParams = '';
    /**
	 * @type {any[]}
	 */
    let links = [];
  
    onMount(() => {
      const updateState = () => {
        currentPath = window.location.pathname;
        queryParams = window.location.search;
        updateLinks();
      };
  
      updateState();
  
      window.addEventListener('popstate', updateState);
      window.addEventListener('pushstate', updateState);
  
      return () => {
        window.removeEventListener('popstate', updateState);
        window.removeEventListener('pushstate', updateState);
      };
    });
  
    /**
     * @param {string} route
     */
    function preserveQuery(route) {
      return queryParams ? `${route}${queryParams}` : route;
    }
  
    function updateLinks() {
      links = pages.map(pageItem => ({
        ...pageItem,
        href: preserveQuery(pageItem.route),
      }));
    }
  </script>
  
  <style>
    ul {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      list-style-type: none;
      padding: 0;
      margin: 0;
      background-color: #2c3e50;
      font-family: Arial, sans-serif;
    }
  
    li {
      padding: 0;
      margin: 0;
    }
  
    a {
      text-decoration: none;
    }
  
    button {
      background: none;
      border: none;
      padding: 15px 20px;
      cursor: pointer;
      color: #ffffff;
      font-family: inherit;
      transition: background-color 0.3s;
      text-align: left;
      width: 100%;
      outline: none;
    }
  
    button:hover {
      background-color: #34495e;
    }
  
    button.active {
        text-decoration: underline;
        background-color: #34495e;
        font-weight: bold;
        color: white;
    }
  
    @media (max-width: 767px) {
      button {
        padding: 10px 12px;
      }
    }
  </style>
  
  <ul>
    {#each links as linkItem}
      <li>
        <a href={linkItem.href}>
          <button
            class:active={currentPath === linkItem.route}
          >
            {linkItem.title}
          </button>
        </a>
      </li>
    {/each}
  </ul>
  