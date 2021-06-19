<template>
    <b-card no-body>
        <b-card-header class="border-0">
            <h3 class="mb-0">Tableau des missions </h3>
        </b-card-header>

        <el-table class="table-responsive table"
                  header-row-class-name="thead-light"
                  :data="tripinfo">
            <el-table-column label="Automobile"
                             min-width="310px"
                             prop="vehicle">
                <template v-slot="{row}">
                    <b-media no-body class="align-items-center">
                        <a href="#" class="avatar rounded-circle mr-3">
                            <img alt="Image placeholder" :src="row.img">
                        </a>
                        <b-media-body>
                            <span class="font-weight-600 name mb-0 text-sm">{{row.vehicle}}</span>
                        </b-media-body>
                    </b-media>
                </template>
            </el-table-column>
            <el-table-column label="Conducteur"
                             prop="driver"
                             min-width="140px">
            </el-table-column>

            <el-table-column label="Référence"
                             min-width="170px"
                             prop="reference">

            </el-table-column>

            <el-table-column label="Permanente ou non"
                             min-width="190px"
                             prop="is_permanent">

            </el-table-column>

            <el-table-column label="Début"
                             prop="start_date"
                             min-width="120px">

            </el-table-column>
            <el-table-column label="Fin"
                           prop="end_date"
                           min-width="120px">

            </el-table-column>
        </el-table>

        <b-card-footer class="py-4 d-flex justify-content-end">
            <base-pagination v-model="currentPage" :per-page="10" :total="50"></base-pagination>
        </b-card-footer>
    </b-card>
</template>
<script>
  import { Table, TableColumn} from 'element-ui'
  const axios = require('axios').default;
  export default {
    name: 'trip-table',
    components: {
      [Table.name]: Table,
      [TableColumn.name]: TableColumn
    },
    data() {
      let tripinfo;
      return {
        tripinfo,
        currentPage: 1
      };
    },
    mounted () {
      axios
        .get('http://127.0.0.1:8000/api/trip/missions/')
        .then(response => (this.tripinfo = response.data))
    }
  }
</script>
