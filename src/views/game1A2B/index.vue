<script>
export default {
  name: '',
  data(){
    return{
      input: null,
      answer: null,
      message: '',
      answerList:[],
      aCount:0,
      bCount:0,
      isWrong:false
    }
  },
  methods:{
    submit(){
      let regExp = /^(?!.*(.).*\1)([0-9]+){4}$/
      console.log(regExp.test(this.input))
      if(regExp.test(this.input)){
        this.isWrong = false
        this.aCount = 0
        this.bCount = 0
        for(let i = 0; i < 4; i++){
          let answerNum = this.answer.split('')
          if(this.input.split('').indexOf(answerNum[i]) === i)this.aCount++
          else if(this.input.split('').indexOf(answerNum[i]) != -1) this.bCount++
        }
        this.message = this.aCount+'A'+this.bCount+'B'
        this.answerList.push(this.input+"/"+this.message)
      }
      else{
        this.isWrong = true
      }
    }
    
      
  },
  mounted:function(){
    for(let i = 0; i < 4; i++){
      let num = Math.floor(Math.random()*10)+''
      if(this.answer){
        while(this.answer.split('').indexOf(num) != -1){
          num = Math.floor(Math.random()*10)+''
        }
        this.answer += num
      }
      else this.answer=num
    }
    
  }
}
</script>

<template src="./template.html" />
<style src="./style.scss" lang="scss" />
