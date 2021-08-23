<template>
  <div>
    <div class="row">
      <div class="col-sm-8">
        <div class="text-h4 main-title q-mb-lg">Dashboard</div>
      </div>
      <div class="col-sm-4 col-xs-12">
        <q-card>
          <q-item>
            <q-item-section side>
              <q-icon size="sm" name="img:icons/ic_calendar.png" />
            </q-item-section>
            <q-item-section side>
              Period
            </q-item-section>
            <q-item-section>
                <div class="calendar-periode">
                  <vue-rangedate-picker @selected="onDateSelected" :captions="captions" i18n="EN" righttoleft="true">
                  </vue-rangedate-picker>
                </div>
            </q-item-section>
          </q-item>
        </q-card>
      </div>
    </div>
    
    <q-item dense v-ripple class="bg-primary text-white q-mb-md">
      <q-item-section class="text-weight-bold">MARKET INSIGHTS</q-item-section>
      <q-item-section side>
        <q-item dense clickable v-ripple class="bg-primary text-white">
          <q-item-section class="q-pr-sm" side>
            <q-icon size="xs" name="img:icons/ic_help.png" />
          </q-item-section>
          <q-item-section side class="text-white text-caption q-pr-sm">
            Click Here for Help
          </q-item-section>
          <q-item-section side class="q-pa-none">
            <q-icon color="white" size="xs" name="expand_less" />
          </q-item-section>
        </q-item>
      </q-item-section>
    </q-item>

    <div class="row q-mb-md">
      <div class="col-sm-3">
        <q-card flat bordered>
          <q-card-section class="q-pr-xs">
            <q-item class="q-pa-none">
              <q-item-section>
                <div class="text-caption text-grey">
                  Sales Turnover
                </div>
                <div class="text-h6 text-weight-bold`">Rp 3.600.000</div>
                <div class="text-xsmall text-grey">
                  <span class="text-negative text-weight-bold">
                    <q-icon size="xs" name="south" /> 13.8%
                  </span>
                  last period in product sold
                </div>
              </q-item-section>
              <q-item-section class="q-pr-sm" side>
                <q-icon size="xl" name="img:icons/ic_sales-turnover.svg" />
              </q-item-section>
              <q-item-section class="q-pr-sm" side top>
                <q-btn flat icon="more_vert" padding="xs" />
              </q-item-section>
            </q-item>
          </q-card-section>
        </q-card>
      </div>
    </div>

    <div class="row q-col-gutter-md items-stretch">
      <div class="col-sm-6 col-xs-12">
        <q-card flat bordered class="full-height">
          <q-card-section class="q-pb-none">
            <q-item class="q-pa-none">
              <q-item-section>
                <div class="text-h6">AVERAGE PURCHASE VALUE</div>
              </q-item-section>
              <q-item-section side>
                <q-select
                  dense
                  outlined
                  use-input
                  fill-input
                  hide-selected
                  placeholder="Select"
                  v-model="model"
                  style="width: 120px"
                  :options="options"  />
              </q-item-section>
              <q-item-section side>
                <q-btn flat icon="more_vert" padding="xs" />
              </q-item-section>
            </q-item>
          </q-card-section>
          <q-card-section>
            <apexchart type="bar" width="80%" height="250" :options="chartOptions" :series="series"></apexchart>
          </q-card-section>
        </q-card>
      </div>
      <div class="col-sm-3 col-xs-12">
        <q-card flat bordered class="full-height">
          <q-card-section class="q-pb-none">
            <q-item class="q-pa-none">
              <q-item-section>
                <div class="text-h6">BEST SELLING SKU</div>
              </q-item-section>
              <q-item-section side>
                <q-btn flat icon="more_vert" padding="xs" />
              </q-item-section>
            </q-item>
          </q-card-section>
          <q-card-section class="q-gutter-sm">
            <template v-for="item in items">
              <q-card flat bordered class="rounded-borders">
                <q-card-section class="q-py-none">
                  <q-item class="q-pa-none">
                    <q-item-section thumbnail>
                      <img style="width: 60px" class="full-height" src="img/sample-product.png">
                    </q-item-section>
                    <q-item-section>
                      <q-item-label>{{ item.productName }}</q-item-label>
                      <q-item class="q-pa-none" style="min-height: 0">
                        <q-item-section>
                          <q-item-label caption>{{ item.price }}</q-item-label>
                        </q-item-section>
                        <q-item-section>
                          <q-item-label caption>{{ item.qty }}</q-item-label>
                        </q-item-section>
                      </q-item>
                    </q-item-section>
                  </q-item>
                </q-card-section>
              </q-card>
            </template>
          </q-card-section>
        </q-card>
      </div>

      <div class="col-sm-3 col-xs-12">
        <q-card flat bordered class="full-height">
          <q-card-section class="q-pb-none">
            <q-item class="q-pa-none">
              <q-item-section>
                <div class="text-h6">TOP COMPETITOR SKU</div>
              </q-item-section>
              <q-item-section side>
                <q-btn flat icon="more_vert" padding="xs" />
              </q-item-section>
            </q-item>
          </q-card-section>
          <q-card-section class="q-gutter-sm">
            <template v-for="item in items">
              <q-card flat bordered class="rounded-borders">
                <q-card-section class="q-py-none">
                  <q-item class="q-pa-none">
                    <q-item-section thumbnail>
                      <img style="width: 60px" class="full-height" src="img/sample-product.png">
                    </q-item-section>
                    <q-item-section>
                      <q-item-label>{{ item.productName }}</q-item-label>
                      <q-item class="q-pa-none" style="min-height: 0">
                        <q-item-section>
                          <q-item-label caption>{{ item.price }}</q-item-label>
                        </q-item-section>
                        <q-item-section>
                          <q-item-label caption>{{ item.qty }}</q-item-label>
                        </q-item-section>
                      </q-item>
                    </q-item-section>
                  </q-item>
                </q-card-section>
              </q-card>
            </template>
          </q-card-section>
        </q-card>
      </div>
    </div>
  </div>
</template>

<script>
import VueApexCharts from 'vue-apexcharts'
import VueRangedatePicker from 'vue-rangedate-picker'
export default {
  name: 'PageIndex',
  components: {
    apexchart: VueApexCharts,
    VueRangedatePicker 
  },
  data () {
    return {
      selectedDate: {
        start: '',
        end: ''
      },
      captions: {
        title: '',
        ok_button: 'Apply'
      },

      options: [
        'Last 6 months'
      ],

      items: [
        { productName: '[Nama Product]', price: 'Rp XXXX', qty: '[jml terjual]'  },
        { productName: '[Nama Product]', price: 'Rp XXXX', qty: '[jml terjual]'  },
        { productName: '[Nama Product]', price: 'Rp XXXX', qty: '[jml terjual]'  },
        { productName: '[Nama Product]', price: 'Rp XXXX', qty: '[jml terjual]'  },
      ],
      
      series: [{
        name: 'Average',
        data: [44, 55, 41, 67, 22, 43]
      }, {
        name: 'Gross',
        data: [10, 10, 10, 10, 10, 10]
      }],
      chartOptions: {
        chart: {
          type: 'bar',
          height: 300,
          stacked: true,
          toolbar: {
            show: false
          },
          zoom: {
            enabled: false
          }
        },
        colors:['#37B04C', '#279D44'],
        dataLabels: {
          enabled: false
        },
        responsive: [{
          breakpoint: 480,
          options: {
            legend: {
              position: 'bottom',
              offsetY: 10
            }
          }
        }],
        plotOptions: {
          bar: {
            horizontal: false,
            columnWidth: '30%',
          },
        },
        xaxis: {
          categories: ['Jan 12', 'Tue', 'Wed', 'Thu',
            'Fri', 'Sat'
          ],
        },
        legend: {
          position: 'bottom',
          offsetY: 10
        },
        fill: {
          opacity: 1
        }
    },
    }
  },
  methods: {
    onDateSelected: function (daterange) {
      this.selectedDate = daterange
    }
  }
}
</script>

<style lang="scss" scooped>
.main-title {
  font-size: 2.5rem;
  color: #707070;
  font-weight: 600
}
.text-xsmall {
  font-size: 10px
}
.calendar-periode {
  .calendar-root {
    .input-date {
      border: 0 !important;
      width: 100%
    }
  }
  .calendar_days li {
    line-height: 2.2em;
    height: 26.8px;
    border-radius: 50%
  }
  li.calendar_days_selected,
  li.calendar_days_in-range {
    background: #d6edda !important;
    color: $primary !important;
    font-weight: bold
  }
  .calendar-wrap {
    float: right !important
  }
  .calendar-range {
    border-left: 0 !important;
    border-right: 1px solid #ccc !important;
    
  }
  .calendar-btn-apply {
    background: $primary !important;
    cursor: pointer;
    padding: 0 !important
  }
  .active-preset[data-v-5e837f70] {
    border: 1px solid $primary !important;
    color: $primary !important;
  }
}
</style>
