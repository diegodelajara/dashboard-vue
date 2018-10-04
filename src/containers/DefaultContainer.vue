<template>
  <div class="app">
    <AppHeader fixed>
      <SidebarToggler class="d-lg-none" display="md" mobile />
      <b-link class="navbar-brand" to="/dashboard">
        <img class="navbar-brand-full" src="img/brand/logo.svg" width="89" height="25" alt="CoreUI Logo">
        <img class="navbar-brand-minimized" src="img/brand/sygnet.svg" width="30" height="30" alt="CoreUI Logo">
      </b-link>
      <SidebarToggler class="d-md-down-none" display="lg" />
      <b-navbar-nav class="d-md-down-none">
        <!--b-nav-item class="px-3">Ajustes</b-nav-item-->
      </b-navbar-nav>
      <b-navbar-nav class="ml-auto">
        <b-nav-item class="d-md-down-none">
          <i class="icon-bell"></i>
          <b-badge pill variant="danger">5</b-badge>
        </b-nav-item>
        <DefaultHeaderDropdownAccnt/>
      </b-navbar-nav>
    </AppHeader>
    <div class="app-body">
      <AppSidebar fixed>
        <SidebarHeader/>
        <SidebarForm/>
        <SidebarNav :navItems="navItems"></SidebarNav>
        <!--SidebarNav :navItems="nav"></SidebarNav-->
        <SidebarFooter/>
        <SidebarMinimizer/>
      </AppSidebar>
      <main class="main">
        <Breadcrumb :list="list"/>
        <div class="container-fluid">
          <router-view></router-view>
        </div>
      </main>
    </div>
    
  </div>
</template>

<script>
//import nav from '@/_nav'
import {  Header as AppHeader, 
          SidebarToggler,
          Sidebar as AppSidebar,
          SidebarFooter,
          SidebarForm,
          SidebarHeader,
          SidebarMinimizer,
          SidebarNav,
          Breadcrumb
        } from '@coreui/vue'

import DefaultAside from './DefaultAside'

import DefaultHeaderDropdownAccnt from './DefaultHeaderDropdownAccnt'

export default {
  name: 'full',
  components: {
    AppHeader,
    AppSidebar,
    Breadcrumb,
    DefaultAside,
    DefaultHeaderDropdownAccnt,
    SidebarForm,
    SidebarFooter,
    SidebarToggler,
    SidebarHeader,
    SidebarNav,
    SidebarMinimizer
  },
  data () {
    return {
      navItems: [
        {
          // Contabilidad
          icon: "fa fa-calculator",
          name: "Contabilidad",
          children: [
            {
              icon: "fa fa-dollar",
              name: "Ingresos",
              url: "/contabilidad-ingresos"
            },{
              icon: "fa fa-dollar",
              name: "Egresos",
              url: "/contabilidad-egresos"
            },{
              icon: "icon-puzzle",
              name: "Multas",
              url: "/contabilidad-multas"
            },{
              icon: "icon-puzzle",
              name: "Condonaciones",
              url: "/contabilidad-condonaciones"
            }
          ]
        },{
          // GGCC
          icon: "fa fa-percent",
          name: "Gastos Comunes",
          url: "/gastos-comunes"
        },{
          // Nómina y Remuneraciones
          icon: "fa fa-table",
          name: "Nómina y Remuneraciones",
          children: [{
              icon: "fa fa-dollar",
              name: "Nómina",
              url: "/nomina"
            },{
              icon: "fa fa-dollar",
              name: "Remuneraciones",
              url: "/remuneraciones"
            },{
              icon: "icon-puzzle",
              name: "Horas trabajadas",
              url: "/horas-trabajadas"
          }]
        },{
          // Proveedores y Mantenciones
          icon: "fa fa-wrench",
          name: "Proveedores y Mantenciones",
          children: [{
              icon: "fa fa-dollar",
              name: "Proveedores",
              url: "/proveedores"
            },{
              icon: "fa fa-dollar",
              name: "Mantenciones",
              url: "/mantenciones"
            }]
        },{
          // Residentes y Visitas
          icon: "fa fa-users",
          name: "Residentes y Visitas",
          url: "/residentes",
          children: [{
              icon: "fa fa-dollar",
              name: "Residentes",
              url: "/residentes"
            },{
              icon: "fa fa-dollar",
              name: "Visitas",
              url: "/visitas"
            }]
        },{
          // Mensajes
          icon: "fa fa-envelope-o",
          name: "Mensajes",
          url: "/mensajes"
        },{
          // Seguridad y Alertas
          icon: "fa fa-warning",
          name: "Seguridad y Alertas",
          url: "/segiridad-y-alertas"
        },{
          // Espacios Comunes
          icon: "fa fa-map-marker",
          name: "Espacios Comunes",
          url: "/widgets"
        },{
          // Biblioteca
          icon: "fa fa-book",
          name: "Biblioteca",
          url: "/widgets"
        }
      ],
      //nav: nav.items
    }
  },
  computed: {
    name () {
      return this.$route.name
    },
    list () {
      return this.$route.matched.filter((route) => route.name || route.meta.label )
    }
  }
}
</script>

<style>
  .sidebar .nav-dropdown > .nav-dropdown-items{
    padding-left: 18px;
    background-color: #3a4248;
  }
</style>
