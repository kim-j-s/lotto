<template>
  <header>1등 가즈아~~</header>
  <div class="content">
    <ul class="chkList">
      <li v-for="(item, index) in numList" :key="index">
        <label>
          <input
            type="checkbox"
            name=""
            id=""
            :checked="item.isChecked"
            v-model="item.isChecked"
            :disabled="item.isDisabled"
          />
          <span class="text">{{ item.text }}</span>
          <i></i>
        </label>
      </li>
    </ul>
    <div class="btnarea">
      <VInput
        v-model="inputValue"
        inpClass="tac"
        types="number"
        maxlengths="8"
        placeholder="횟수 입력"
      />
      <VButton text="여러번 돌리기" @click="action" />
    </div>
    <div class="btnarea">
      <VButton text="걍 뽑기" @click="action2" />
    </div>
    <div class="btnarea">
      <VButton text="초기화" @click="reset" />
    </div>
    <div class="rst">
      <span class="tit"> 결과 : </span>
      <!-- <div class="rstBox"> -->
      <VRst :전달값="sendValue" />
      <!-- </div> -->
    </div>

    <VPopup />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import VButton from './components/VButton.vue'
import VInput from './components/VInput.vue'
import VRst from './components/VRst.vue'
import VPopup from './components/VPopup.vue'

// set
let sendValue = ref([])
const inputValue = ref()

const numList = ref([
  {
    text: '1'
  },
  {
    text: '2'
  },
  {
    text: '3'
  },
  {
    text: '4'
  },
  {
    text: '5'
  },
  {
    text: '6'
  },
  {
    text: '7'
  },
  {
    text: '8'
  },
  {
    text: '9'
  },
  {
    text: '10'
  },
  {
    text: '11'
  },
  {
    text: '12'
  },
  {
    text: '13'
  },
  {
    text: '14'
  },
  {
    text: '15'
  },
  {
    text: '16'
  },
  {
    text: '17'
  },
  {
    text: '18'
  },
  {
    text: '19'
  },
  {
    text: '20'
  },
  {
    text: '21'
  },
  {
    text: '22'
  },
  {
    text: '23'
  },
  {
    text: '24'
  },
  {
    text: '25'
  },
  {
    text: '26'
  },
  {
    text: '27'
  },
  {
    text: '28'
  },
  {
    text: '29'
  },
  {
    text: '30'
  },
  {
    text: '31'
  },
  {
    text: '32'
  },
  {
    text: '33'
  },
  {
    text: '34'
  },
  {
    text: '35'
  },
  {
    text: '36'
  },
  {
    text: '37'
  },
  {
    text: '38'
  },
  {
    text: '39'
  },
  {
    text: '40'
  },
  {
    text: '41'
  },
  {
    text: '42'
  },
  {
    text: '43'
  },
  {
    text: '44'
  },
  {
    text: '45'
  }
])

// 다회차
const action = () => {
  // console.log('inputValue.value : ', inputValue.value)
  // 반복횟수 설정
  if (inputValue.value === undefined || inputValue.value === '') {
    // console.log('값이 undefined 이거나 없는 경우 ')
    inputValue.value = '1'
  }
  const rollingCnt = inputValue.value

  // 쓰까에서 필요한 값 들

  const 쓰까 = function () {
    // console.log('쓰까 돌아요')
    // numList 의 text 값을 배열로 받아보기
    // numList.value.forEach(item => {
    //   console.log(item.text);
    // });
    // numList의 checked된 값을 filter로 가져오고 map을 사용하여 text를 추출
    const printCheckedText = numList.value.filter((item) => item.isChecked).map((item) => item.text)
    // console.log('선택 된 checkbox : ', printCheckedText);

    // numList의 text 값을 모두 추출
    const 전체배열 = numList.value.map((item) => item.text)
    // console.log('전체 배열 : ', 전체배열);
    const 추출 = 전체배열.filter((item) => !printCheckedText.includes(item))
    // console.log('추출 : ',추출);

    // 5개 추출
    let val = []
    let 추출값가공 = 추출
    // console.log('가공될 추출 값 : ',추출값가공);
    for (var i = 0; i < 6; i++) {
      // console.log('기본 val : ', val);
      // 섞기
      const 랜덤값얻기 = 추출[Math.floor(Math.random() * 추출.length)]
      // console.log('얻은 랜덤 값 : ', 랜덤값얻기)
      val.push(랜덤값얻기)

      // 동일한 값을 배열 위치 찾기
      const 가공할꺼 = 추출값가공.indexOf(랜덤값얻기)
      // console.log('가공할꺼 : ', 가공할꺼);

      // 찾은 배열의 index에 해당하는 값을 제거
      추출값가공.splice(가공할꺼, 1)
      // console.log('가공된거 : ', 추출값가공);
    }
    // 오름차순 정렬
    val.sort(function (a, b) {
      return a - b
    })
    // console.log(' --- 결과 --- ', val)
    // sendValue.value = val
    sendValue.value.push(val)
    console.log(' --- 결과 --- ', sendValue.value)

    // 원본 리스트를 forEach로 돌려서 item의 값과 배열의 값이 동일하면 checked 상태로 변경
    for (var i = 0; i < 6; i++) {
      numList.value.forEach((item) => {
        // console.log(item.text);
        // console.log('까꿍 : ', val[i]);
        if (item.text === val[i]) {
          // console.log('까꿍 : ',item.text, val[i]);
          item.isChecked = true
        }
      })
    }
  }

  // 반복 출력
  for (var roll = 0; roll < rollingCnt; roll++) {
    // action()
    쓰까()
  }
  inputValue.value = ''
}

// 단식
const action2 = () => {
  sendValue.value = []
  // numList의 text 값을 모두 추출
  const 전체배열 = numList.value.map((item) => item.text)
  // console.log('전체 배열 : ', 전체배열)

  // 5개 추출
  const 쓰까 = function () {
    let val = []
    let 추출값가공 = 전체배열
    // console.log('가공될 추출 값 : ',추출값가공);
    for (var i = 0; i < 6; i++) {
      // console.log('기본 val : ', val);
      // 섞기
      const 랜덤값얻기 = 전체배열[Math.floor(Math.random() * 전체배열.length)]
      // console.log('얻은 랜덤 값 : ', 랜덤값얻기)
      val.push(랜덤값얻기)

      // 동일한 값을 배열 위치 찾기
      const 가공할꺼 = 추출값가공.indexOf(랜덤값얻기)
      // console.log('가공할꺼 : ', 가공할꺼)

      // 찾은 배열의 index에 해당하는 값을 제거
      추출값가공.splice(가공할꺼, 1)
      // console.log('가공된거 : ', 추출값가공);
    }
    // 오름차순 정렬
    val.sort(function (a, b) {
      return a - b
    })
    // console.log(' --- 결과 --- ', val)
    // sendValue.value = val
    sendValue.value.push(val)
  }
  쓰까()
}

// 초기화
const reset = () => {
  numList.value.forEach((item) => {
    item.isChecked = false
  })
  inputValue.value = ''
  sendValue.value = []
}

const up = (value) => {
  inputValue.value = value
}
</script>

<style lang="scss" scoped></style>
