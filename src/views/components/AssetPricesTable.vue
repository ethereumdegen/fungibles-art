<template>
  <div class=" ">
     <table class="table-auto w-full text-gray-500">
          <thead>
            <tr>
              <th style="text-align:left"  > Asset Name  </th>

              <th style="text-align:left"  > Current Price </th>


              <th style="text-align:left"  >   </th>
               
            </tr>
          </thead>
          <tbody v-cloak>
            <tr v-for="row of coinDataArray" class="text-white  border-2 border-gray-500 cursor-pointer " @click="clickedRow(row)">
               
              <td style="text-align:left" class="py-8 px-2">   {{ row.name  }} (ERC20) </td>

              <td style="text-align:left" >   {{ row.priceRatio.toFixed(2)  }} ETH </td>

               <td style="text-align:left" class="hover:bg-gray-500" >  
                  <a v-bind:href="'https://app.sushi.com/swap?outputCurrency='+row.contractAddress" target="_blank">
                    <svg class="svg-icon" viewBox="0 0 20 20">
                    <path d="M6.634,13.591H2.146c-0.247,0-0.449,0.201-0.449,0.448v2.692c0,0.247,0.202,0.449,0.449,0.449h4.488c0.247,0,0.449-0.202,0.449-0.449v-2.692C7.083,13.792,6.881,13.591,6.634,13.591 M6.185,16.283h-3.59v-1.795h3.59V16.283zM6.634,8.205H2.146c-0.247,0-0.449,0.202-0.449,0.449v2.692c0,0.247,0.202,0.449,0.449,0.449h4.488c0.247,0,0.449-0.202,0.449-0.449V8.653C7.083,8.407,6.881,8.205,6.634,8.205 M6.185,10.897h-3.59V9.103h3.59V10.897z M6.634,2.819H2.146c-0.247,0-0.449,0.202-0.449,0.449V5.96c0,0.247,0.202,0.449,0.449,0.449h4.488c0.247,0,0.449-0.202,0.449-0.449V3.268C7.083,3.021,6.881,2.819,6.634,2.819 M6.185,5.512h-3.59V3.717h3.59V5.512z M15.933,5.683c-0.175-0.168-0.361-0.33-0.555-0.479l1.677-1.613c0.297-0.281,0.088-0.772-0.31-0.772H9.336c-0.249,0-0.448,0.202-0.448,0.449v7.107c0,0.395,0.471,0.598,0.758,0.326l1.797-1.728c0.054,0.045,0.107,0.094,0.161,0.146c0.802,0.767,1.243,1.786,1.243,2.867c0,1.071-0.435,2.078-1.227,2.837c-0.7,0.671-1.354,1.086-2.345,1.169c-0.482,0.041-0.577,0.733-0.092,0.875c0.687,0.209,1.12,0.314,1.839,0.314c0.932,0,1.838-0.173,2.673-0.505c0.835-0.33,1.603-0.819,2.262-1.449c1.322-1.266,2.346-2.953,2.346-4.751C18.303,8.665,17.272,6.964,15.933,5.683 M15.336,14.578c-1.124,1.077-2.619,1.681-4.217,1.705c0.408-0.221,0.788-0.491,1.122-0.812c0.97-0.929,1.504-2.168,1.504-3.485c0-1.328-0.539-2.578-1.521-3.516c-0.178-0.17-0.357-0.321-0.548-0.456c-0.125-0.089-0.379-0.146-0.569,0.041L9.769,9.327v-5.61h5.861l-1.264,1.216c-0.099,0.094-0.148,0.229-0.137,0.366c0.014,0.134,0.088,0.258,0.202,0.332c0.313,0.204,0.61,0.44,0.882,0.7c1.158,1.111,2.092,2.581,2.092,4.145C17.405,12.026,16.48,13.482,15.336,14.578"></path>
                  </svg> 
                </a>


              </td>


                <td style="text-align:left"  class="hover:bg-gray-500" >  
                     <a v-bind:href="'https://etherscan.io/address/'+row.sushiPair"  target="_blank">

                <svg class="svg-icon" viewBox="0 0 20 20">
                  <path fill="none" d="M1.729,9.212h14.656l-4.184-4.184c-0.307-0.306-0.307-0.801,0-1.107c0.305-0.306,0.801-0.306,1.106,0
                  l5.481,5.482c0.018,0.014,0.037,0.019,0.053,0.034c0.181,0.181,0.242,0.425,0.209,0.66c-0.004,0.038-0.012,0.071-0.021,0.109
                  c-0.028,0.098-0.075,0.188-0.143,0.271c-0.021,0.026-0.021,0.061-0.045,0.085c-0.015,0.016-0.034,0.02-0.051,0.033l-5.483,5.483
                  c-0.306,0.307-0.802,0.307-1.106,0c-0.307-0.305-0.307-0.801,0-1.105l4.184-4.185H1.729c-0.436,0-0.788-0.353-0.788-0.788
                  S1.293,9.212,1.729,9.212z"></path>
                </svg>

                 </a>
              </td>

              
              
            </tr>
             
          </tbody>
        </table>

        <div v-if="!coinDataArray || coinDataArray.length == 0" v-cloak>
          No records found.
        </div>
  </div>
</template>


<script>


export default {
  name: 'AssetPricesTable',
  props: ['coinDataArray'],
  data() {
    return {

    }
  },
  created(){

  },
  methods: {
      clickedRow(row){
        this.clickedRowCallback(row)
      } 
  }
}
</script>
