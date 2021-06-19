<template>
  <div>
    <base-header class="pb-6 pb-8 pt-5 pt-md-8 bg-gradient-success">
    <!--base-header class="pb-6"-->
      <!--b-row align-v="center" class="py-4">
        <b-col lg="6" cols="7">
          <h6 class="h2 text-white d-inline-block mb-0">Default</h6>
          <nav aria-label="breadcrumb" class="d-none d-md-inline-block ml-md-4">
            <route-bread-crumb></route-bread-crumb>
          </nav>
        </b-col>
        <b-col lg="6" cols="5" class="text-right">
          <base-button size="sm" type="neutral">New</base-button>
          <base-button size="sm" type="neutral">Filters</base-button>
        </b-col>
      </b-row-->
      <!-- Card stats -->
      <b-row >
        <b-col xl="3" md="6" >
          <stats-card title="Effectif Total Du Parc "
                      type="gradient-red"
                      sub-title="350,897"
                      icon="ni ni-active-40">

            <template slot="footer">
              <span class="text-success mr-2"><i class="fa fa-arrow-up"></i> 3.48%</span>
              <span class="text-nowrap">Depuis l'année dernière</span>
            </template>
          </stats-card>
        </b-col>
        <b-col md="6" xl="3">
          <stats-card title="Coût Total Carburant"
                      type="gradient-orange"
                      sub-title="2,356"
                      icon="ni ni-chart-pie-35">

            <template slot="footer">
              <span class="text-success mr-2"><i class="fa fa-arrow-up"></i> 12.18%</span>
              <span class="text-nowrap">Depuis le mois dernier</span>
            </template>
          </stats-card>
        </b-col>
        <b-col md="6" xl="3">
          <stats-card title="Coût Total Maintenance"
                      type="gradient-green"
                      sub-title="925"
                      icon="ni ni-money-coins">

            <template slot="footer">
              <span class="text-danger mr-2"><i class="fa fa-arrow-down"></i> 5.72%</span>
              <span class="text-nowrap">Depuis le mois dernier</span>
            </template>
          </stats-card>

        </b-col>
        <b-col md="6" xl="3">
          <stats-card title="Coût Total Autre frais "
                      type="gradient-info"
                      sub-title="66,65%"
                      icon="ni ni-chart-bar-32">

            <template slot="footer">
              <span class="text-success mr-2"><i class="fa fa-arrow-up"></i> 54.8%</span>
              <span class="text-nowrap">Depuis le mois dernier</span>
            </template>
          </stats-card>
        </b-col>
      </b-row>
    </base-header>
    <b-container fluid class="mt--7">
      <b-row class="starter-page">
        <b-col>
          <fleet-table/>
        </b-col>
      </b-row>
    </b-container>

  </div>
</template>
<script>
  import RouteBreadCrumb from '@/components/Breadcrumb/RouteBreadcrumb';
  import StatsCard from '@/components/Cards/StatsCard';
  import {Table, TableColumn} from "element-ui";
  import FleetTable from "@/views/Flotte/FleetTable";

  export default {
    name: 'fleet-page',
    components: {
      StatsCard,
      RouteBreadCrumb,
      FleetTable,
      [Table.name]: Table,
      [TableColumn.name]: TableColumn
    },
    data() {
      return {

      };
    }
  };
</script>
<style>
  .fleet-page {
    min-height: calc(100vh - 380px);
  }
</style>
