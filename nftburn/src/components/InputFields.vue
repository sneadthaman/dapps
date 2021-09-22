<template>
  <div class="inputs">
    <input v-model='contractInput' type='text' id='contractInput' placeholder='0x12345...'/>
    <label for='contractInput' name='contractInput'>Contract Address</label>
    <input v-model='tokenIdInput' type='text' id='tokenIdInput' placeholder='12345'/>
    <label for='tokenIdInput' name='tokenIdInput'>Token ID</label>
    <a @click='checkOwnership' href="#" class="square_btn">Check Ownership</a>
  </div>
</template>

<script>
import Web3 from 'web3'
import $ from 'jquery'

export default{
  name: 'input-fields',
  data(){
    return{
      contractInput: null,
      tokenIdInput: null,
      abi: []
    }
  },
  methods:{
    async checkOwnership(contractInput, tokenIdInput) {
      this.abi = this.getContractABI(contractInput)
      console.log('ABI: ' + this.abi)
      const web3 = new Web3(Web3.givenProvider)
      const contract = new web3.eth.Contract(this.abi)
      const owner = await contract.methods.ownerOf(tokenIdInput).call()
    },
    getContractABI(contractInput) {
      const web3 = new Web3(new Web3.providers.HttpProvider())
      console.log('Retrieving JSON...')
      console.log('Contract: '+ this.contractInput)
      $.getJSON('https://api.etherscan.io/api?module=contract&action=getabi&address='+this.contractInput+'&apikey=PXU6TCNGPKJKVQV4P4P8NFC76KFPIQURRE', function (data) {
        this.contractABI = JSON.parse(data.result);
        console.log(this.contractABI)
    //   if (this.contractABI != ''){
    //     var MyContract = new web3.eth.Contract(this.contractABI);
    //     var myContractInstance = MyContract.at(this.contractInput);
    //     var result = myContractInstance.memberId(this.contractInput);
    //     console.log("result1 : " + result);            
    //     var result = myContractInstance.members(1);
    //     console.log("result2 : " + result);
    //   } else {
    //     console.log("Error" );
    // }            
      })
        return this.contractABI
    }
  }
}
</script>

<style scoped>
  .inputs {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  input {
    min-height: 2.5rem;
    width: 80%;
    margin: 0 auto;
    padding: 1rem;
  }
  label {
    margin: 1rem auto;
    font-size: 1.25rem;
  }

  .square_btn {
    display: inline-block;
    padding: 7px 20px;
	  border-radius: 25px;
    text-decoration: none;
    color: #FFF;
    background-image: -webkit-linear-gradient(45deg, #FFC107 0%, #ff8b5f 100%);
    background-image: linear-gradient(45deg, #FFC107 0%, #ff8b5f 100%);
    transition: .4s;
    width: 25%;
    margin: 2rem auto;
    text-align: center;
    font-weight: bold;
}

.square_btn:hover {
    background-image: -webkit-linear-gradient(45deg, #FFC107 0%, #f76a35 100%);
    background-image: linear-gradient(45deg, #FFC107 0%, #f76a35 100%);
}
</style>
