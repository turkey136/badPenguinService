<template>
  <div>
    <v-container>
      <v-row justify="center">
        <v-col cols="12">
          <v-form ref="form" @submit.prevent="exec">
            <v-col cols="12">
              <h1>投資皮算用計算機</h1>
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
            <v-col cols="12">
              <h4>金融商品投資条件</h4>
            </v-col>
            <v-col cols="6">
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
                      <input v-model="data[0].amount" placeholder="0" id="amount" />円
                    </label>
                  </div>
                  <div>
                    <label>
                      <span>分配金</span>
                      <input v-model="data[0].returnAmount" placeholder="0" id="returnAmount" />円
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
            <v-col cols="6">
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
            　        <input v-model="data[1].amount" placeholder="0" id="amount" />円
            　      </label>
            　    </div>
            　    <div>
            　      <label>
            　        <span>分配金</span>
            　        <input v-model="data[1].returnAmount" placeholder="0" id="returnAmount" />円
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
            <v-col cols="6">
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
                    <input v-model="data[2].amount" placeholder="0" id="amount" />円
                  </label>
                </div>
                <div>
                  <label>
                    <span>分配金</span>
                    <input v-model="data[2].returnAmount" placeholder="0" id="returnAmount" />円
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
            <v-col cols="6">
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
                    <input v-model="data[3].amount" placeholder="0" id="amount" />円
                  </label>
                </div>
                <div>
                  <label>
                    <span>分配金</span>
                    <input v-model="data[3].returnAmount" placeholder="0" id="returnAmount" />円
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
            <v-col cols="12">
            <button type="submit">計算する</button>
            </v-col>
          </v-form>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import AmountInput from "@/components/math_allocation/amount_input";

export default {
  components: {
    AmountInput
  },
  data() {
    return {
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
    exec: function() {
      console.log(this.base);
      console.log(this.data);
    }
  }
};
</script>
