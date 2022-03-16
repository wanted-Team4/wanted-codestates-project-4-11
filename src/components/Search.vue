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
      <div class="selectedDiv" v-if="selectedCompany">
        <span>{{ selectedCompany }}</span>
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
  data() { 
    return { 
      keyWord: "", 
      company: ["삼성전자", "카카오", "LG"],
      suggestion: [],
      selectedCompany: "", 
    }; 
  }, 
  methods: { 
    resetSelectedCompany () {
      this.selectedCompany = "";
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
      this.selectedCompany = e.target.innerText;
      this.keyWord = "";
    }
  },
  components: {},
};
</script>

<style>
.wrapper {
  width: 350px;
  display: flex;
  flex-direction: column;
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
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
}

.searchInput {
  padding-left: 10px;
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
  list-style: none;
  position: relative;
  margin: 0;
  padding: 10px 0px 10px 0px;
  margin: 0px 15px 0px 15px;
  border-top: 1px solid #646464;
}

.suggestion {
  padding-left: 10px;
  font-size: 1rem;
  height: 13px;
  padding: 10px 10px 5px 5px;
  height: 30px;
}

.suggestion:hover{
  background-color: #D2D2D2;
}

</style>