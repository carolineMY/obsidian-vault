
### html
```
  <div class="statistic_wrap">

      <div class="statistic_info">

        <div class="statistic_total">

          <img

            src="~@/assets/images/onlineSale/delivered.png"

            class="statistic_img"

          />

          <div>

            <span class="statistic_item_label">已发货</span>

            <CountTo

              custom-class="statistic_item_value"

              :target-value="120"

            />

          </div>

        </div>

        <div class="statistic_item">

          <span class="statistic_item_label">视频号禾量</span>

          <CountTo

            custom-class="statistic_item_value"

            :target-value="80"

          />

        </div>

        <div class="statistic_item">

          <span class="statistic_item_label">抖店</span>

          <CountTo

            custom-class="statistic_item_value"

            :target-value="40"

          />

        </div>

      </div>

    </div>
```
  
### css

.statistic_wrap {

  display: flex;

  margin-bottom: 16px;

  gap: 16px;

}

.statistic_info {

  flex: 1;

  background-color: #fff;

  display: flex;

  align-items: center;

  padding: 16px 0 16px 24px;

  border-radius: 6px;

}

.statistic_total {

  display: flex;

  width: 40%;

  border-right: 1px solid #e7e7e7;

  

  .statistic_img {

    width: 56px;

    height: 56px;

    margin-right: 24px;

  }

}

.statistic_item {

  padding-left: 24px;

  flex: 1;

}

.statistic_item_label {

  line-height: 22px;

  font-size: 14px;

  color: #000000a6;

}

.statistic_item_value {

  margin-top: 8px;

  font-size: 30px;

  font-weight: bold;

  color: #000000d9;

  line-height: 30px;

}