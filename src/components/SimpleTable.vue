<template>
  <v-container>
    <v-layout
      text-center
      wrap
    >
      <v-flex md12>
        <span style="font-size:35px,">
          EVENTOS
        </span>
      </v-flex>
      <v-flex md12>
        <v-text-field
          v-model="semesterYearSelected"
          label="Semestre/ano"
          @keyup.enter.native="changeData()"
        />
      </v-flex>
      <v-flex md12>
        <v-data-table
          :headers="headers"
          :items="data"
          item-key="name"
          class="elevation-1"
          :loading="loading"
        >
          <template slot="item" slot-scope="props">
              <tr @click="rowClick(props.item.ID)">
                  <td class="text-xs-left">
                    <span>
                      HOLA
                    </span>
                    {{ props.item.ID }}
                  </td>
                  <td class="text-xs-left">{{ props.item.DESCRICAO }}</td>
                  <td class="text-xs-left">{{ props.item.PERIODO }}</td>
                  <td class="text-xs-left">{{ props.item.DATA_IMPRESSAO }}</td>
              </tr>
          </template>
        </v-data-table>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>

export default {
  data: () => ({
    semesterYearSelected: '',
    loading: false,
    selectedItem: 'Sample',
    pagination: {
        sortBy: 'ID'
    },
    headers: [
        { text: 'ID', value: 'ID', align: 'center', width: '10%' },
        { text: 'Descrição', value: 'DESCRICAO', align: 'left', width: '60%' },
        { text: 'Período', value: 'PERIODO', align: 'left', width: '20%' },
        {
            text: 'Data Impressão',
            value: 'DATA_IMPRESSAO',
            align: 'left',
            width: '10%'
        }
    ],
    data: []
  }),
  mounted () {
    this.loadData()
  },
  methods: {
    rowClick (id) {
      console.log(id)
    },
    changeData () {
      let newData = [
        {
          'ID': 5,
          'DESCRICAO': 'COISA BRASILEIRA',
          'PERIODO': '03/12/2019-04/12/2019',
          'DATA_IMPRESSAO': '06/12/2019'
        },
        {
          'ID': 6,
          'DESCRICAO': 'COISA BRASILEIRAss',
          'PERIODO': '03/12/2019-04/12/2019',
          'DATA_IMPRESSAO': '06/12/2019'
        },
        {
          'ID': 7,
          'DESCRICAO': 'COISA BRASILEIRA',
          'PERIODO': '03/12/2019-04/12/2019',
          'DATA_IMPRESSAO': '06/12/2019'
        },
        {
          'ID': 8,
          'DESCRICAO': 'COISA BRASILEIRA',
          'PERIODO': '03/12/2019-04/12/2019',
          'DATA_IMPRESSAO': '06/12/2019'
        }
      ]

      this.data = newData
    },
    async getEventos() {
      // const sql = await fs
      //   .readFileSync(path.join(process.env.ROOT_PATH, 'src/db/sql/get-evento.sql'))
      //   .toString()
      //   return await db.getData(sql, [process.env.ANO_SEM])
      return [
        {
          'ID': 1,
          'DESCRICAO': 'MUITO SAUDADE',
          'PERIODO': '03/12/2019-04/12/2019',
          'DATA_IMPRESSAO': '06/12/2019'
        },
        {
          'ID': 2,
          'DESCRICAO': 'MUITO SAUDADE',
          'PERIODO': '03/12/2019-04/12/2019',
          'DATA_IMPRESSAO': '06/12/2019'
        },
        {
          'ID': 3,
          'DESCRICAO': 'MUITO SAUDADE',
          'PERIODO': '03/12/2019-04/12/2019',
          'DATA_IMPRESSAO': '06/12/2019'
        },
        {
          'ID': 4,
          'DESCRICAO': 'MUITO SAUDADES',
          'PERIODO': '03/12/2019-04/12/2019',
          'DATA_IMPRESSAO': '06/12/2019'
        }
      ]
    },
    async loadData() {
      this.data = await this.getEventos()
    }
  }
}
</script>
