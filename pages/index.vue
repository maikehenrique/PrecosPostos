<template>
  <div>
    <div class="marketing">
      <div class="content-marketing">
        <h1>
          Uma simples ferramenta para te ajudar a<br /><span>economizar.</span>
        </h1>
        <p class="description">
          Aqui você pode acompanhar os preços das suas empresas preferidas e
          escolher qual cabe em seu bolso
        </p>
        <div class="icons-left">
          <img alt="logo" src="../static/m1.png" />
        </div>
      </div>
    </div>
    <div>
      <div class="card">
        <DataTable
          :value="customers"
          :paginator="true"
          class="p-datatable-customers"
          show-gridlines
          :rows="10"
          data-key="id"
          :filters.sync="filters"
          filter-display="menu"
          :loading="loading"
          responsive-layout="stack"
          :global-filter-fields="[
            'posto',
            'etanol',
            'gasolinac',
            'gasolinaa',
            'diesel',
            'diesels10',
          ]"
        >
          <template #header>
            <div class="flex justify-content-between">
              <span class="p-input-icon-left">
                <i class="pi pi-search" />
                <InputText
                  v-model="filters['global'].value"
                  placeholder="Pesquise"
                />
              </span>
            </div>
          </template>
          <template #empty> No customers found. </template>
          <template #loading> Loading customers data. Please wait. </template>
          <Column field="posto" header="Posto" sortable>
            <template #body="slotProps">
              <div class="font-bold w-10">
                {{ slotProps.data[slotProps.column.field] }}
              </div>
            </template>
          </Column>
          <Column field="etanol" header="Etanol" sortable>
            <template #body="slotProps">
              {{ formatMoeda(slotProps.data[slotProps.column.field]) }}
            </template>
          </Column>
          <Column field="gasolinac" header="Gasolina Comum" sortable>
            <template #body="slotProps">
              {{ formatMoeda(slotProps.data[slotProps.column.field]) }}
            </template>
          </Column>
          <Column field="gasolinaa" header="Gasolina Aditivada" sortable>
            <template #body="slotProps">
              {{ formatMoeda(slotProps.data[slotProps.column.field]) }}
            </template>
          </Column>
          <Column field="diesel" header="Diesel" sortable>
            <template #body="slotProps">
              {{ formatMoeda(slotProps.data[slotProps.column.field]) }}
            </template>
          </Column>
          <Column field="diesels10" header="Diesel s10" sortable>
            <template #body="slotProps">
              {{ formatMoeda(slotProps.data[slotProps.column.field]) }}
            </template>
          </Column>
          <Column field="atualizacao" header="Atualizado" sortable>
            <template #body="slotProps">
              {{ formatMoeda(slotProps.data[slotProps.column.field]) }}
            </template>
          </Column>
        </DataTable>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      customers: [
        {
          posto: 'Posto 2000',
          etanol: 5.199,
          gasolinac: 7.599,
          gasolinaa: 7.699,
          diesel: 6.799,
          diesels10: 6.749,
          atualizacao: '24/03/2022',
        },
        {
          posto: 'Posto Avenida',
          etanol: 5.498,
          gasolinac: 7.998,
          gasolinaa: 8.198,
          diesel: 6.898,
          diesels10: 6.998,
          atualizacao: '24/03/2022',
        },
        {
          posto: 'Posto Brasil',
          etanol: 4.919,
          gasolinac: 7.309,
          gasolinaa: 7.309,
          diesel: 6.649,
          diesels10: 6.699,
          atualizacao: '24/03/2022',
        },
        {
          posto: 'Posto Caçula',
          etanol: 5.199,
          gasolinac: 7.699,
          gasolinaa: 7.699,
          diesel: 6.79,
          diesels10: 6.898,
          atualizacao: '24/03/2022',
        },
        {
          posto: 'Posto Capuano',
          etanol: 5.197,
          gasolinac: 7.548,
          gasolinaa: '-',
          diesel: 6.747,
          diesels10: 6.867,
          atualizacao: '24/03/2022',
        },
        {
          posto: 'Posto Copas',
          etanol: 5.499,
          gasolinac: 7.999,
          gasolinaa: 8.149,
          diesel: 6.749,
          diesels10: 6.849,
          atualizacao: '24/03/2022',
        },
        {
          posto: 'Posto Econômico',
          etanol: 5.399,
          gasolinac: 7.899,
          gasolinaa: 7.899,
          diesel: 6.699,
          diesels10: 6.799,
          atualizacao: '24/03/2022',
        },
        {
          posto: 'Posto Flamir (Carajás)',
          etanol: 5.38,
          gasolinac: 7.87,
          gasolinaa: 7.87,
          diesel: 6.72,
          diesels10: 6.82,
          atualizacao: '24/03/2022',
        },
        {
          posto: 'Posto Jamaica',
          etanol: 5.397,
          gasolinac: 7.997,
          gasolinaa: 8.197,
          diesel: 6.798,
          diesels10: 6.898,
          atualizacao: '24/03/2022',
        },
        {
          posto: 'Posto Jandaia',
          etanol: 5.099,
          gasolinac: 7.559,
          gasolinaa: 7.559,
          diesel: 6.699,
          diesels10: 6.799,
          atualizacao: '24/03/2022',
        },
        {
          posto: 'Posto Morada Nova',
          etanol: 5.099,
          gasolinac: 7.659,
          gasolinaa: '-',
          diesel: 6.799,
          diesels10: 6.849,
          atualizacao: '24/03/2022',
        },
        {
          posto: 'Posto Pampa',
          etanol: 5.29,
          gasolinac: 7.79,
          gasolinaa: 7.79,
          diesel: 6.74,
          diesels10: 6.89,
          atualizacao: '24/03/2022',
        },
        {
          posto: 'Posto Rota do sol',
          etanol: 5.439,
          gasolinac: 7.829,
          gasolinaa: 7.829,
          diesel: 6.599,
          diesels10: 6.699,
          atualizacao: '24/03/2022',
        },
        {
          posto: 'Posto São Francisco',
          etanol: 5.199,
          gasolinac: 7.599,
          gasolinaa: 7.599,
          diesel: 6.799,
          diesels10: 6.899,
          atualizacao: '24/03/2022',
        },
        {
          posto: 'Posto São Vicente',
          etanol: 5.099,
          gasolinac: 7.599,
          gasolinaa: '-',
          diesel: 6.699,
          diesels10: '-',
          atualizacao: '24/03/2022',
        },
        {
          posto: 'Posto Serra Negra',
          etanol: 5.499,
          gasolinac: 7.998,
          gasolinaa: 8.199,
          diesel: 6.748,
          diesels10: 6.848,
          atualizacao: '24/03/2022',
        },
        {
          posto: 'Posto União',
          etanol: 5.498,
          gasolinac: 7.998,
          gasolinaa: 8.198,
          diesel: 6.898,
          diesels10: 6.998,
          atualizacao: '24/03/2022',
        },
      ],
      filters: {
        global: {},
      },
      loading: true,
    }
  },
  created() {},
  mounted() {
    this.loading = false
  },
  methods: {
    filterDate(value, filter) {
      if (
        filter === undefined ||
        filter === null ||
        (typeof filter === 'string' && filter.trim() === '')
      ) {
        return true
      }

      if (value === undefined || value === null) {
        return false
      }

      return value === this.formatDate(filter)
    },
    formatDate(date) {
      let month = date.getMonth() + 1
      let day = date.getDate()

      if (month < 10) {
        month = '0' + month
      }

      if (day < 10) {
        day = '0' + day
      }

      return date.getFullYear() + '-' + month + '-' + day
    },
    formatMoeda(value) {
      return value.toLocaleString('pt-BR', {
        style: 'currency',
        currency: 'BRL',
      })
    },
  },
}
</script>
