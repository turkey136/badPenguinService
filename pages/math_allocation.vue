<template>
  <div>
    <v-container>
      <v-form ref="form">
        <v-row>
          <v-col cols="12">
            <h1>投資皮算用計算機 v0.0.0</h1>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12">
            <div>
              <h4>投資条件</h4>
              <div>
                <label>
                  <span>積み立て投資額</span>
                  <input v-model="base.baseAmount" type="text" />
                </label>
              </div>
              <div>
                <label>
                  <span>増資タイミング</span>
                  <select v-model="base.addTiming" id="timing">
                    <option value="1">毎月</option>
                    <option value="2">隔月</option>
                    <option value="3">初回のみ</option>
                  </select>
                </label>
              </div>
            </div>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12">
            <h4>金融商品投資条件</h4>
          </v-col>
        </v-row>
        <v-row>
          <v-col sm="12" md="6">
            <div>
              <h4>金融商品1</h4>
              <div>
                <div>
                  <label>
                    <span>金融商品</span>
                    <input v-model="data[0].name" type="text" />
                  </label>
                </div>
                <div>
                  <label>
                    <span>評価額</span>
                    <input
                      v-model="data[0].amount"
                      placeholder="0"
                      id="amount"
                    />円
                  </label>
                </div>
                <div>
                  <label>
                    <span>分配金</span>
                    <input
                      v-model="data[0].returnAmount"
                      placeholder="0"
                      id="returnAmount"
                    />円
                  </label>
                </div>
                <div>
                  <label>
                    <span>分配タイミング</span>
                    <select v-model="data[0].timing" id="returnType">
                      <option value="1">毎月</option>
                      <option value="2">隔月</option>
                      <option value="3">年4回</option>
                      <option value="4">年2回</option>
                    </select>
                  </label>
                </div>
              </div>
            </div>
          </v-col>
          <v-col sm="12" md="6">
            <div>
              <h4>金融商品2</h4>
              <div>
                <div>
                  <label>
                    <span>金融商品</span>
                    <input v-model="data[1].name" type="text" />
                  </label>
                </div>
                <div>
                  <label>
                    <span>評価額</span>
                    <input
                      v-model="data[1].amount"
                      placeholder="0"
                      id="amount"
                    />円
                  </label>
                </div>
                <div>
                  <label>
                    <span>分配金</span>
                    <input
                      v-model="data[1].returnAmount"
                      placeholder="0"
                      id="returnAmount"
                    />円
                  </label>
                </div>
                <div>
                  <label>
                    <span>分配タイミング</span>
                    <select v-model="data[1].timing" id="returnType">
                      <option value="1">毎月</option>
                      <option value="2">隔月</option>
                      <option value="3">年4回</option>
                      <option value="4">年2回</option>
                    </select>
                  </label>
                </div>
              </div>
            </div>
          </v-col>
        </v-row>
        <v-row>
          <v-col sm="12" md="6">
            <div>
              <h4>金融商品3</h4>
              <div>
                <div>
                  <label>
                    <span>金融商品</span>
                    <input v-model="data[2].name" type="text" />
                  </label>
                </div>
                <div>
                  <label>
                    <span>評価額</span>
                    <input
                      v-model="data[2].amount"
                      placeholder="0"
                      id="amount"
                    />円
                  </label>
                </div>
                <div>
                  <label>
                    <span>分配金</span>
                    <input
                      v-model="data[2].returnAmount"
                      placeholder="0"
                      id="returnAmount"
                    />円
                  </label>
                </div>
                <div>
                  <label>
                    <span>分配タイミング</span>
                    <select v-model="data[2].timing" id="returnType">
                      <option value="1">毎月</option>
                      <option value="2">隔月</option>
                      <option value="3">年4回</option>
                      <option value="4">年2回</option>
                    </select>
                  </label>
                </div>
              </div>
            </div>
          </v-col>
          <v-col sm="12" md="6">
            <div>
              <h4>金融商品4</h4>
              <div>
                <div>
                  <label>
                    <span>金融商品</span>
                    <input v-model="data[3].name" type="text" />
                  </label>
                </div>
                <div>
                  <label>
                    <span>評価額</span>
                    <input
                      v-model="data[3].amount"
                      placeholder="0"
                      id="amount"
                    />円
                  </label>
                </div>
                <div>
                  <label>
                    <span>分配金</span>
                    <input
                      v-model="data[3].returnAmount"
                      placeholder="0"
                      id="returnAmount"
                    />円
                  </label>
                </div>
                <div>
                  <label>
                    <span>分配タイミング</span>
                    <select v-model="data[3].timing" id="returnType">
                      <option value="1">毎月</option>
                      <option value="2">隔月</option>
                      <option value="3">年4回</option>
                      <option value="4">年2回</option>
                    </select>
                  </label>
                </div>
              </div>
            </div>
          </v-col>
        </v-row>
        <v-row>
          <v-col  sm="12" md="6">
            <v-btn @click="exec">計算する</v-btn>
          </v-col>
        </v-row>
      </v-form>
      <v-row>
        <v-col cols="12">
          <div v-if="errors.length > 0">
            <error v-for="error in errors" :key="error">
              {{ error }}
            </error>
          </div>
          <div v-if="errors.length === 0 && chartdata.datasets.length > 0">
            <p>
              商品を追加する場合は「追加」 -> 「計算する」押下 ->
              「表示中の金融商品名」2回押下で対応してください
            </p>
            <p>再描画がうまくいかんのです</p>
            <LineChart :chart-data="chartdata" :options="options" />
          </div>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import LineChart from "@/components/LineChart.vue";
export default {
  components: {
    LineChart
  },
  data() {
    return {
      Accumulation: false,
      chartdata: {
        labels: ["1", "2", "3", "4", "5", "6", "7", "8", "9", "10", "11", "12"],
        datasets: []
      },
      options: {
        responsive: true,
        maintainAspectRatio: false
      },
      errors: [],
      base: {
        baseAmount: 0,
        addTiming: "1"
      },
      data: [
        {
          name: "",
          timing: "1",
          amount: 0,
          returnAmount: 0
        },
        {
          name: "",
          timing: "1",
          amount: 0,
          returnAmount: 0
        },
        {
          name: "",
          timing: "1",
          amount: 0,
          returnAmount: 0
        },
        {
          name: "",
          timing: "1",
          amount: 0,
          returnAmount: 0
        },
        {
          name: "",
          timing: "1",
          amount: 0,
          returnAmount: 0
        }
      ]
    };
  },
  methods: {
    clear: function() {
      this.errors = [];
      this.base.baseAmount = 0;
      this.data.forEach(element => {
        element.amount = 0;
        element.returnAmount = 0;
        element.name = 0;
      });
    },
    exec: function() {
      this.errors = [];
      if (this.chartdata.datasets.length > 0) {
        this.chartdata.datasets.splice(0);
      }

      if (Number(this.base.baseAmount) == 0) {
        this.errors.push(
          "積み立て投資額がマイナスまたは未入力なので計算できません"
        );
      }
      let viewdata = [];
      this.data.forEach(element => {
        if (Number(element.amount) > 0 && Number(element.returnAmount) > 0) {
          element.amount = Number(element.amount);
          element.returnAmount = Number(element.returnAmount);
          if (element.name === "") {
            element.name = `評価額 ${element.amount} の商品`;
          }
          this.chartdata.datasets.push({
            label: [element.name],
            data: this.mothReturnAmount(element),
            backgroundColor: this.lineColer()
          });
        }
      });
      console.log(this.chartdata.datasets);
      if (this.chartdata.datasets.length === 0) {
        this.errors.push(
          "評価額と分配金が全項目でマイナスまたは未入力なので計算できません"
        );
      }
    },
    lineColer: function() {
      switch (this.chartdata.datasets.length) {
        case 0:
          return "#a9a9a9";
          break;
        case 1:
          return "#6495ed";
          break;
        case 2:
          return "#00ff7f";
          break;
        case 3:
          return "#ff69b4";
          break;
      }
    },
    mothReturnAmount: function(element) {
      let data = [];
      let unit = Math.floor((this.base.baseAmount / element.amount) * 10000);
      for (let count = 1; count < 13; ) {
        if (
          element.timing === "1" ||
          (element.timing === "2" && count % 2 === 0) ||
          (element.timing === "3" && count % 4 === 0) ||
          (element.timing === "4" && count % 6 === 0)
        ) {
          // 毎月配当 || 隔月配当 |
          const returnAmount = Math.floor(
            (unit / 10000) * element.returnAmount
          );
          if (this.Accumulation) {
            // 累積額
            if (count === 1) {
              data.push(returnAmount);
            } else {
              data.push(returnAmount + data.slice(-1)[0]);
            }
          } else {
            // 月額
            data.push(returnAmount);
          }
          unit = unit + Math.floor((returnAmount / element.amount) * 10000);
        } else {
          data.push(0);
        }

        // 翌月分の増資処理
        if (
          this.base.addTiming === "1" ||
          (this.base.addTiming === "2" && count % 2 === 0)
        ) {
          unit =
            unit + Math.floor((this.base.baseAmount / element.amount) * 10000);
        }
        count++;
      }

      return data;
    }
  }
};
</script>
<style lang="scss" scoped>
error {
  color: #fff;
  background-color: #f10e0e;
  font-size: 15px;
  font-weight: bold;
}
</style>
