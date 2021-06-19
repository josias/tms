<template>
    <b-card no-body>
        <b-card-header class="border-0">
            <h3 class="mb-0">Tableau de la flotte </h3>
        </b-card-header>

        <el-table class="table-responsive table"
                  header-row-class-name="thead-light"
                  :data="info">
            <el-table-column label="Automobile"
                             min-width="310px"
                             prop="name">
                <template v-slot="{row}">
                    <b-media no-body class="align-items-center">
                        <a href="#" class="avatar rounded-circle mr-3">
                            <img alt="Image placeholder" :src="row.img">
                        </a>
                        <b-media-body>
                            <span class="font-weight-600 name mb-0 text-sm">{{row.name}}</span>
                        </b-media-body>
                    </b-media>
                </template>
            </el-table-column>
            <el-table-column label="Marque"
                             prop="firm"
                             min-width="140px">
            </el-table-column>

            <el-table-column label="Numéro"
                             min-width="170px"
                             prop="registration_number">

            </el-table-column>

            <el-table-column label="Type"
                             min-width="190px"
                             prop="fuel_type">

            </el-table-column>

            <el-table-column label="Consommation (L/100)"
                             prop="fuel_consumption"
                             min-width="240px">

            </el-table-column>
        </el-table>

        <b-card-footer class="py-4 d-flex justify-content-end">
            <base-pagination v-model="currentPage" :per-page="10" :total="50"></base-pagination>
        </b-card-footer>
    </b-card>
</template>
<script>
  import projects from './../Tables/projects'
  import { Table, TableColumn} from 'element-ui'
  const axios = require('axios').default;
  export default {
    name: 'fleet-table',
    components: {
      [Table.name]: Table,
      [TableColumn.name]: TableColumn
    },
    data() {
      let info;
      return {
        info,
        projects,
        currentPage: 1
      };
    },
    mounted () {
      axios
        .get('http://127.0.0.1:8000/api/fleet/cars')
        .then(response => (this.info = response.data))
    }
  }
</script>
