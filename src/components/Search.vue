<template>
  <div class="wrapper">
    <div class="resultDiv">
      <div class="resultLeft">
        <span>검색 결과</span>
         <svg
            width="6"
            height="10"
            viewBox="0 0 6 10"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M1 1L5 5L1 9"
              stroke="#727272"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
      </div>
      <div class="selectedDiv" v-if="select">
        <span>{{ select }}</span>
        <button class="resetButton" @click="resetSelectedCompany" >
          <svg 
            xmlns="http://www.w3.org/2000/svg" 
            width="30"
            height="30"
            viewBox="0 0 30 30"
            style="fill:#D2D2D2;"
          >
            <path d="M15,3C8.373,3,3,8.373,3,15c0,6.627,5.373,12,12,12s12-5.373,12-12C27,8.373,21.627,3,15,3z M16.414,15 c0,0,3.139,3.139,3.293,3.293c0.391,0.391,0.391,1.024,0,1.414c-0.391,0.391-1.024,0.391-1.414,0C18.139,19.554,15,16.414,15,16.414 s-3.139,3.139-3.293,3.293c-0.391,0.391-1.024,0.391-1.414,0c-0.391-0.391-0.391-1.024,0-1.414C10.446,18.139,13.586,15,13.586,15 s-3.139-3.139-3.293-3.293c-0.391-0.391-0.391-1.024,0-1.414c0.391-0.391,1.024-0.391,1.414,0C11.861,10.446,15,13.586,15,13.586 s3.139-3.139,3.293-3.293c0.391-0.391,1.024-0.391,1.414,0c0.391,0.391,0.391,1.024,0,1.414C19.554,11.861,16.414,15,16.414,15z">
            </path>
          </svg>
        </button>
      </div>
    </div>
    <div class="searchDiv">
      <input
        class="searchInput"
        type="text"
        placeholder="기업명을 검색하세요"
        :value="keyWord"
        @keyup="onKeyupHandler"
      />
      <ul class="suggestions" v-if="keyWord.length !== 0">
        <li
          v-for="(item, i) of suggestion"
          v-bind:key="i"
          class="suggestion"
          @click="onClickHandler"
        >
          {{ item }}
        </li>
        <li class="suggestion" v-if="suggestion.length === 0">
          일치하는 기업명이 없습니다.
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  props: ["selectedCompany"],
  data() { 
    return { 
      keyWord: "", 
      company: ["삼성전자", "카카오", "LG"],
      suggestion: [],
      select: this.selectedCompany,
    }; 
  }, 
  methods: { 
    resetSelectedCompany () {
      this.select = "";
      this.$emit('changeSelect', "");
    },
    onKeyupHandler (e) {
      this.keyWord = e.target.value;
      this.suggestion = [];
      this.company.map((word) => {
        if(word.includes(this.keyWord.toUpperCase()) || word.includes(this.keyWord.toLowerCase())){
            this.suggestion.push(word);
          }
        }
      )
    },
    onClickHandler (e) {
      this.select = e.target.innerText;
      this.$emit('changeSelect', e.target.innerText);
      this.keyWord = "";
    }
  },
  components: {},
};
</script>

<style>
.wrapper {
  width: 500px;
  display: flex;
  flex-direction: column;
  margin: auto;
  margin-bottom: 20px;
}

.resultDiv {
  height: 35px;
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}

.resultLeft {
  display: flex;
  align-items: center;
}

.resultLeft > span {
  color: #727272;
  font-weight: bold;
  font-size: 1.2rem;
  margin-right: 5px;
}

.selectedDiv{
  display: flex;
  align-items: center;
  color: #646464;
}

.selectedDiv > button {
  cursor: pointer;
  border: none;
  background-color: white;
  padding: 0;
}


.searchDiv {
  border: 1px solid #F2F2F2;
  background-color: #F8F8F8;
  border-radius: 5px;
  box-sizing: border-box;
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
}

.searchInput {
  padding-left: 10px;
  width: 490px;
  box-sizing: border-box;
  border: none;
  background-color: transparent;
  padding: 20px 0px 20px 10px;
  font-size: 1rem;
}

.searchDiv > input:focus {
  outline: none;
}

.suggestions {
  width: 500px;
  list-style: none;
  position: absolute;
  box-sizing: border-box;
  border: 1px solid #F2F2F2;
  z-index: 8;
  padding: 10px 10px 10px 10px;
  margin: 0;
  background-color: white;
  border-radius: 5px;
}

.suggestions::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  display: block;
  width: calc(100%);
  border-bottom: 1px solid black;
}

.suggestion {
  vertical-align: baseline;
  padding-left: 5px;
  font-size: 1rem;
}

.suggestion:hover{
  background-color: #D2D2D2;
}

</style>