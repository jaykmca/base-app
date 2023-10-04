<template>
    
    <aside class="sidebar">
      <h2 class="menu-title">Main App</h2>
      
      <div class="submenu-container" @mouseenter="showSubmenu('appone')" @mouseleave="hideSubmenu()" >
        <div class="menu-item active-menu-item">
          App One
        </div>
        <div class="submenu"  v-if="activeSubmenu === 'appone'">
          <div class="submenu-item">
            <ul>
                <li  @click="navigate('/appone/home')">Home</li> 
                <li  @click="navigate('appone/about')">About</li>
                <li  @click="navigate('appone/contact')" >Contact</li>  
            </ul>
              
          </div>
        </div>
      </div>

      <div style="height: 90px"></div>
     

    
      
      <div class="submenu-container" @mouseenter="showSubmenu('apptwo')" @mouseleave="hideSubmenu()" >
        <div class="menu-item active-menu-item">
          App two
        </div>
        <div class="submenu" v-if="activeSubmenu === 'apptwo'">
          <div class="submenu-item">
            <ul>
                <li  @click="navigate('apptwo/home')">Home</li> 
                <li  @click="navigate('apptwo/about')">About</li>
                <li  @click="navigate('apptwo/contact')" >Contact</li>  
            </ul>
              
          </div>
        </div>
      </div>
          
    </aside>
  </template>
  <script>
  export default {
    // methods: {
    //   navigate(path) {
    //     console.log("sidebarmenu-----", path)
    //     // Use the Vue Router to navigate to the specified path
    //     this.$router.push(path);
    //   },
    // },
    name: 'SideBarMenu',
        data() {
        return {
            //submenuVisible: false,
            activeSubmenu: null,
            
            
        };
        },
        methods: {
        navigate(path) {
        // Update the URL in the iframe
        this.$emit('iframe-navigation', path);
        },
        showSubmenu(menu) {
            //this.submenuVisible = true;
            this.activeSubmenu = menu;

        }, 
         hideSubmenu() {
           //    //this.submenuVisible = false;
           this.activeSubmenu = null;
           
           
          }
        
        },
  };
  </script>
  
  <style scoped>
 .sidebar {
  width: 170px;
  background-color: #333;
  color: #fff;
  padding: 20px;
  height: 100%; /* Set the height to 100% */
  position: fixed; /* Keep the sidebar fixed on the page */
  top: 0; /* Position it at the top of the page */
  left: 0; /* Position it at the left of the page */
  overflow-y: auto; /* Add scroll if content overflows */
}
   
  .sidebar ul {
    list-style: none;
    padding: 0;
  }
  
  .sidebar li {
    margin-bottom: 10px;
    cursor: pointer;
  }
  
  .sidebar li:hover {
    text-decoration: underline;
  } 

  .menu-title {
    font-weight: bold;
    margin-bottom: 15px; /* Add margin at the bottom of the title */
    margin-top: 15px;
    font-size: 18px; /* Increase font size for the title */
  }

  .menu-item {
   color: #fff;
   text-decoration: none;
   padding: 10px;
   margin-bottom: 5px; /* Add margin between menu items */
   transition: background-color 0.3s; /* Add smooth background color transition */
   border-radius: 5px; /* Add rounded corners to menu items */
}

.submenu-container {
    position: relative;
  }

  .menu-item:hover {
    background-color: #555;
  }

    
  /* Style for submenu */
  .submenu {
    display: none;
    position: absolute;
    top: 100%;
    left: 0;
    background-color: #444;
    width: 167px;
    border-left: 2px solid #666;
    border-radius: 5px
   
  }
  .submenu-item {
    color: #444;;
    padding: 8px;
    text-align: center;
    background-color: #fff;
    text-decoration: none;
  }
  .submenu-container:hover .submenu {
    display: block;
  }

  .submenu-container.menu-item:hover + .submenu,
  .submenu:hover {
    display: block;
  }
  .active-menu-item {
   font-weight: bold; /* Change the font weight for the active menu item */
   color: #fff; /* Change the text color for the active menu item */
}
  </style>