<template>
  <div><!-- <col id="editor" width="800"> -->
    <div class="container" id="editor" width="800"></div>  

    <div class="container mt-5" width="800" > 
      <div class="input-group mb-3">
        <span class="input-group-text" id="inputGroup-sizing-default">내용</span>
        <input type="text" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default" v-model="newInfo">
      </div>
      <div class="input-group mb-3">
        <span class="input-group-text" id="inputGroup-sizing-default">세부항목</span>
        <input type="text" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default" v-model="newDetail">
      </div>
      <div class="input-group mb-3">
        <span class="input-group-text" id="inputGroup-sizing-default">시작 날짜</span>
        <input type="text" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default" v-model="startDate">
      </div>
      <div class="input-group mb-3">
        <span class="input-group-text" id="inputGroup-sizing-default">종료 날짜</span>
        <input type="text" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default" v-model="endDate">
      </div>
      <button type="submit" class="btn btn-primary" @click="addInfo">저장하기</button>
    </div>   

    <!-- <div class="container" id="chart" width="800">
      <apexchart type="rangeBar" height="800" :options="chartOptions" :series="series" ></apexchart>
    </div> -->
    <div class="container" id="chart" width="800">
        <apexchart type="rangeBar" height="450" :options="chartOptions" :series="series"></apexchart>
      </div>
    
  </div>
</template>

<script>
import Editor from '@toast-ui/editor';
import '@toast-ui/editor/dist/toastui-editor.css'; // Editor's Style
import VueApexCharts from 'vue3-apexcharts';
import moment from "moment";



export default {


  data: function () {
    return {
      editor: null,
      // el: '#app',
      newInfo: "",
      startDate: "",
      endDate: "",
      newDetail: "",
      x: "",
      y:[],
      data:[],
      name: "",
      
      
      components: {
          apexchart: VueApexCharts
        },

      // series: [
      //   {
      //     data: [
      //       {
      //         x: 'Analysis',
      //         y: [
      //           new Date('2019.02.27').getTime(),
      //           new Date('2019-03-04').getTime()
      //         ],
      //         fillColor: '#008FFB'
      //       },
           
      //     ]
      //   }
      // ],
      // chartOptions: {
      //   chart: {
      //     height: 250,
      //     type: 'rangeBar'
      //   },
      //   plotOptions: {
      //     bar: {
      //       horizontal: true,
      //       distributed: true,
      //       dataLabels: {
      //         hideOverflowingLabels: false
      //       }
      //     }
      //   },
      //   dataLabels: {
      //     enabled: true,
      //     formatter: function (val, opts) {
      //       var label = opts.w.globals.labels[opts.dataPointIndex]
      //       var a = moment(val[0])
      //       var b = moment(val[1])
      //       var diff = b.diff(a, 'days')
      //       return label + ': ' + diff + (diff > 1 ? ' days' : ' day')
      //     },
      //     style: {
      //           colors: ['#f3f4f5', '#fff']
      //         }
      //   },
      //   xaxis: {
      //         type: 'datetime'
      //       },
      //       yaxis: {
      //         show: false
      //       },
      //       grid: {
      //         row: {
      //           colors: ['#f3f4f5', '#fff'],
      //           opacity: 1
      //         }
      //       }

      // },
      series: [
            // {
            //   name: 'Bob',
            //   data: [
            //     {
            //       x: 'Design',
            //       y: [
            //         new Date('2019-03-05').getTime(),
            //         new Date('2019-03-08').getTime()
            //       ]
            //     },
                // {
                //   x: 'Code',
                //   y: [
                //     new Date('2019-03-02').getTime(),
                //     new Date('2019-03-05').getTime()
                //   ]
                // },
                // {
                //   x: 'Code',
                //   y: [
                //     new Date('2019-03-05').getTime(),
                //     new Date('2019-03-07').getTime()
                //   ]
                // },
                // {
                //   x: 'Test',
                //   y: [
                //     new Date('2019-03-03').getTime(),
                //     new Date('2019-03-09').getTime()
                //   ]
                // },
                // {
                //   x: 'Test',
                //   y: [
                //     new Date('2019-03-08').getTime(),
                //     new Date('2019-03-11').getTime()
                //   ]
                // },
                // {
                //   x: 'Validation',
                //   y: [
                //     new Date('2019-03-11').getTime(),
                //     new Date('2019-03-16').getTime()
                //   ]
                // },
                // {
                //   x: 'Design',
                //   y: [
                //     new Date('2019-03-01').getTime(),
                //     new Date('2019-03-03').getTime()
                //   ],
                // }
            //   ]
            // },
            //  {
            //    name: 'Joe',
            //    data: [
            //      {
            //        x: 'Design',
            //        y: [
            //          new Date('2019-03-02').getTime(),
            //          new Date('2019-03-05').getTime()
            //        ]
            //      },
            //      {
            //        x: 'Test',
            //        y: [
            //          new Date('2019-03-06').getTime(),
            //          new Date('2019-03-16').getTime()
            //        ],
            //        goals: [
            //          {
            //            name: 'Break',
            //            value: new Date('2019-03-10').getTime(),
            //            strokeColor: '#CD2F2A'
            //          }
            //        ]
            //      },
            //      {
            //        x: 'Code',
            //        y: [
            //          new Date('2019-03-03').getTime(),
            //          new Date('2019-03-07').getTime()
            //        ]
            //      },
            //      {
            //        x: 'Deployment',
            //        y: [
            //          new Date('2019-03-20').getTime(),
            //          new Date('2019-03-22').getTime()
            //        ]
            //      },
            //      {
            //        x: 'Design',
            //        y: [
            //          new Date('2019-03-10').getTime(),
            //          new Date('2019-03-16').getTime()
            //        ]
            //      }
            //    ]
            //  },
            //  {
            //    name: 'Dan',
            //    data: [
            //      {
            //        x: 'Code',
            //        y: [
            //          new Date('2019-03-10').getTime(),
            //          new Date('2019-03-17').getTime()
            //        ]
            //      },
            //      {
            //        x: 'Validation',
            //        y: [
            //          new Date('2019-03-05').getTime(),
            //          new Date('2019-03-09').getTime()
            //        ],
            //        goals: [
            //          {
            //            name: 'Break',
            //            value: new Date('2019-03-07').getTime(),
            //            strokeColor: '#CD2F2A'
            //          }
            //        ]
            //      },
            //    ]
            //  }
          ],
          chartOptions: {
            chart: {
              height: 450,
              type: 'rangeBar'
            },
            plotOptions: {
              bar: {
                horizontal: true,
                barHeight: '80%'
              }
            },
            xaxis: {
              type: 'datetime'
            },
            stroke: {
              width: 1
            },
            fill: {
              type: 'solid',
              opacity: 0.6
            },
            legend: {
              position: 'top',
              horizontalAlign: 'left'
            }
          }

    }
  },
  mounted() {
        this.editor = new Editor({
          el: document.querySelector('#editor'),
          height: '500px',
          initialEditType: 'wysiwyg',
          previewStyle: 'vertical'
        });

      },
  methods: {
    addInfo(){
      console.log(this.newInfo)
      if(this.newInfo == "") {
        alert("내용은 필수 입력값입니다.");
        return;
      }
      if(this.startDate == "") {
        alert("시작 날짜는 필수 입력값입니다.");
        return;
      }
      if(this.endDate == "") {
        alert("종료 날짜는 필수 입력값입니다.");
        return;
      }
      // validation


      // this.series[0].data.push({
      //   x: this.newInfo,
      //   y: [
      //       new Date(this.startDate).getTime(),
      //       new Date(this.endDate).getTime()],
      //   fillColor:  '#008FFB'
      // });
      const ydata = [
        new Date(this.startDate).getTime(),
        new Date(this.endDate).getTime()
      ]

      const inputdata = [
        {
          y : ydata,
          x : this.newDetail
        }
      ]
      

      this.series.push(
        {
          name : this.newInfo,
          data : inputdata
        }
      )

      console.log(this.series)
      console.log(inputdata)

      
      
      // this.series[0].data.push({
       
      //   x: this.newDetail,
      //   y: [
      //       new Date(this.startDate).getTime(),
      //       new Date(this.endDate).getTime()
      //       ]

      // })
      // this.series[0].name = this.newInfo;
      // console.log(this.series);
      this.newInfo= '';
      this.startDate= '';
      this.endDate= '';
      this.newDetail='';
    },
   
  }

}
</script>
