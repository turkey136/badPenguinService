<template>
  <div>
    <v-container>
      <v-row justify="center">
        <v-col cols="12">
          <h1>投資皮算用計算機</h1>
          <div class="baseConditions">
            <h5>投資条件</h5>
            <div>
              <label>
                <span>積み立て投資額</span>
                <input v-model="message" placeholder="10000" id="payment" />円
              </label>
            </div>
            <div>
              <label>
                <span>増資タイミング</span>
                <select v-model="selected" id="timing">
                  <option disabled value="1">毎月</option>
                  <option value="2">隔月</option>
                  <option value="3">初回のみ</option>
                </select>
              </label>
            </div>
          </div>
          <div>
            <h5>投資商品</h5>
            <div class="input_form">
              <div>
                <label>
                  <span>投資信託名</span>
                  <input
                    v-model="payment"
                    placeholder="〇〇Jリート"
                    id="name"
                  />
                </label>
              </div>
              <div>
                <label>
                  <span>評価額</span>
                  <input v-model="payment" placeholder="10000" id="amount" />円
                </label>
              </div>
              <div>
                <label>
                  <span>分配金</span>
                  <input
                    v-model="payment"
                    placeholder="10"
                    id="returnAmount"
                  />円
                </label>
              </div>
              <div>
                <label>
                  <span>分配タイミング</span>
                  <select v-model="selected" id="returnType">
                    <option disabled value="1">毎月</option>
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
    </v-container>
  </div>
</template>

<script>
export default {};
</script>
