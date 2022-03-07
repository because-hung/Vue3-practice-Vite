js 物件取值

Object.entries 把物件轉成陣列
key跟value 都取到  清楚分開
就不用再跑多餘迴圈

大包切成小包
右邊比對陣列去 include 大包的切分小數

動態取值
obj[變數] (創造變數 宣告變數)
obj['變數']  精準取值 
點取值 -> 寫死

forEach

//computed

comA 是 func

comA = result

透過 status 去觀察變化判斷
let status = ref(true)
可以寫操作  單純return 值
而不一定要依賴的元素變化 才能用computed

const comA = computed(() => {
    let result = 0
    console.log('st', status)
if(status.value == true){
     result = 1
    
}else{
      result =  2
}
return result
})


依賴的元素變化

const num = computed(() => {
  return sum.value * 2;
})

/////////////////
object aasign
分層
no index
