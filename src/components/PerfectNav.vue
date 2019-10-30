<template>
  <nav class="navigation">
    <button @click="toggleExpand" :aria-expanded="expanded" aria-controls="menu">
      <svg id="i-menu" aria-label="Menu" viewBox="0 0 32 32" width="16" height="16" fill="none" stroke="#fff" stroke-linecap="round" stroke-linejoin="round" stroke-width="6.25%">
        <path d="M4 8 L28 8 M4 16 L28 16 M4 24 L28 24"></path>
      </svg>
    </button>
    <ul class="menu" :hidden="!expanded">
      <li><a href="/">Home</a></li>
      <li><a href="/benefits">Benefits</a></li>
      <li><a href="/pricing">Pricing</a></li>
      <li><a href="/blog">Blog</a></li>
    </ul>
  </nav>
</template>
<script>
export default {
  name: 'PerfectNav',
  data() {
    return {
      expanded: false
    }
  },
  methods: {
    toggleExpand() {
      this.expanded = !this.expanded
    }
  },
}
</script>
<style>
[hidden] { display: none; }

body {
  overflow: hidden;
}

@media ( max-width: 40rem ) {
  .navigation button {
    display: block;
    position: absolute;
    top: 10px;
    right: 10px;
    border: 0;
    height: 32px;
    width: 32px;
    background: none;
    color: #107db5;
    font-size: 0rem;
    padding: 0;
    transition: 0.2s 0.5s color ease-in-out;
    cursor: pointer;
  }

    .navigation button svg {
      display: block;
      pointer-events: none;
      stroke: currentcolor;
      height: 32px;
      width: 32px;
      transition: 0.2s 0.5s stroke ease-in-out;
    }

    .navigation button::before {
      content: ' ';
      position: absolute;
      border-radius: 200vh;
      opacity: 0;
      left: calc(-130vmax + 50%);
      top: calc(-130vmax + 50%);
      width: 260vmax;
      height: 260vmax;
      background: #107db5;
      display: block;
      z-index: -1;
      -webkit-transform: scale3d(0, 0, 0);
              transform: scale3d(0, 0, 0);
      -webkit-transform-origin: 50% 50%;
              transform-origin: 50% 50%;
      transition: 0.5s ease-in-out transform, 0.2s 0.4s ease-in-out opacity;
    }

    .navigation button[aria\-expanded=true] {
      color: #fff;
    }
    
    .navigation button[aria\-expanded=true]::before {
      opacity: 1;
      -webkit-transform: scale3d(1, 1, 1);
              transform: scale3d(1, 1, 1);
      transition: 0.5s ease-in-out transform, 0.1s ease-in-out opacity;
    }

  .menu {
    pointer-events: none;
    list-style: none;
    width: 100vw;
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-around;
    padding: 0;
  }

    .menu a {
      text-decoration: none;
      font-weight: bold;
      color: #fff;
      opacity: 0;
      display: block;
      -webkit-transform: translateY(-10px);
              transform: translateY(-10px);
      transition: 0.2s 0.5s ease-out opacity, 0.2s 0.5s ease-out transform;
    }

    .menu li:nth-child(2) a {
      transition: 0.2s 0.7s ease-out opacity, 0.2s 0.7s ease-out transform;
    }
    
    .menu li:nth-child(3) a {
      transition: 0.2s 0.9s ease-out opacity, 0.2s 0.9s ease-out transform;
    }
    
    .menu li:nth-child(4) a {
      transition: 0.2s 1.1s ease-out opacity, 0.2s 1.1s ease-out transform;
    }
  
  .menu:not([hidden]) {
    pointer-events: all;
  }
    
    .menu:not([hidden]) a {
      opacity: 1;
      -webkit-transform: translateY(0);
              transform: translateY(0);
    }
}
@media ( min-width: 40rem ) {
  .navigation button { display: none }
  
  .menu {
    width: auto;
    height: auto;
    padding: 0;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-end;
    list-style: none;
    margin: 0;
  }
    
    .menu li {
      padding: 1rem;
    }
      
      .menu li a {
        pointer-events: all;
        opacity: 1;
        -webkit-transform: translateY(0);
                transform: translateY(0);
        font-weight: normal;
        color: #107db5;
        text-decoration: none;
        background: linear-gradient(rgba(16, 125, 181, 0.15), rgba(16, 125, 181, 0.15));
        background-size: 0 100%;
        background-repeat: no-repeat;
        
        padding: 4px;
        margin: -4px;
        border-radius: 2em;
        transition:background .25s ease-out;
      }
        
        .menu li a:hover,
        .menu li a:focus {
          background-size: 100% 100%;
        }
}
</style>