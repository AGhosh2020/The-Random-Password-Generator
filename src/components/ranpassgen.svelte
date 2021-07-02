<script>
    import { range } from 'lodash-es';
	import DarkModeButton from './darkmode.svelte';

    let weak = range(7,16);
    
    let strong = range(16,201);
    
    let toughest = [1024,2048,3072,4096,5120]
    
    let valid = false;
    
    let errors="";

    let no;

    let sym;

    let up;

    let lp;

    let rangenpassword;

    const generate = () =>{
        valid=true;
        let numbers = document.getElementById("numbers");
        let symbols = document.getElementById("symbols");
        let uppercase = document.getElementById("uppercase");
        let lowercase = document.getElementById("lowercase");
        let copythepassword = document.getElementById("copypassauto");
        let retVal = "";
        let passgenlength = document.getElementById("passize").value;
           if(numbers.checked){
               no = "01234567890";
           }
           else{
               no = "";
           }
           if(symbols.checked){
               sym = "@!#$%^&*()*/~{}:'/.,?<>:{}+-?:[]?.,/.,';'][][=-=-*";
           }
           else{
               sym = "";
           }
           if(uppercase.checked){
                up = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
           }    
           else{
               up = "";
           }
           if(lowercase.checked){
               lp = "abcdefghijklmnopqrstuvwxyz";
           }
           else{
               lp = "";
           }
           
           rangenpassword = no+sym+up+lp;

           if(!rangenpassword){
               valid = false;
               errors = "Please select of any 4 options";
           }
           else{
                try{
                    for (var i = 0, n = rangenpassword.length; i < passgenlength; ++i){
                        retVal += rangenpassword.charAt(Math.floor(Math.random() * n));
                    }

                    errors = "";

                    document.getElementById("passgen").value = retVal;

                    if(copythepassword.checked){
                        var RanGenPassword = document.getElementById("passgen");

                        RanGenPassword.select();

                        document.execCommand("copy");
                    }
                }
                catch{
                    errors = "Cannot generate a password. Try generate agains";
                }
           }
    }
    const reset = () => {        
        document.getElementById("passgen").value = "";
        errors = "";
    }
    const CopyToClipboard = () => {
        if(!document.getElementById("passgen").value){
           errors = "Generate Random Password First";
        }
        else{
            var RanGenPassword = document.getElementById("passgen");

            RanGenPassword.select();

            document.execCommand("copy");
        }
    }
</script>

<passgen>
       
         <div>   
            <DarkModeButton/>
        <form>
  
            <label>Password Length :   
                <select autocomplete="off" name="passize" id="passize">
                    <optgroup label="Weak">
                    {#each weak as i}
                            <option value={i}>{i}</option>
                    {/each}
                    </optgroup>
                    <optgroup label="Strong">
                        {#each strong as i}
                        <option value={i}>{i}</option>
                        {/each}
                    
                    </optgroup>
                    <optgroup label="Toughest">
                        {#each toughest as i}
                            <option value={i}>{i}</option>
                        {/each}
                    </optgroup>
            </label>
            <table style="margin-left: auto; margin-right: auto;">
                <tr>
                    <td style="text-align:left;">Include Numbers : </td>
                    <td><input type="checkbox" id="numbers"></td>
                </tr>
                <tr>
                    <td  style="text-align:left;">Include Symbols : </td>
                    <td><input type="checkbox" id="symbols"></td>
                </tr>
                <tr>
                    <td  style="text-align:left;">Include Uppercase : </td>
                    <td><input type="checkbox" id="uppercase"></td>
                </tr>
                <tr>
                    <td style="text-align:left;">Include Lowercase : </td>
                    <td><input type="checkbox" id="lowercase"></td>
                </tr>
                <tr>
                    <td style="text-align: left;">Select the password automatically : </td>
                    <td><input type="checkbox" id="copypassauto"></td>
                </tr>
            </table>
            <div class="but">
                <button type="button" on:click={generate}>Generate</button>
                <button type="button" on:click={reset}>Reset</button> 
                
            </div>
         
        <p>Your new Password : <input type="text" id="passgen" class="passgen" readonly></p>
        <button type="button" on:click={CopyToClipboard}>Copy</button>
        <div class="errors">{errors}</div>
        <p>The random password is generated on the device and not on the server</p>
    </form>
    
</div>
</passgen>

<style>
   .but{
       margin:10px;
   }
   button{
        font-family: 'Josefin Sans', sans-serif;
        padding:10px 10px;
        border:none;
        color: white;
        background:rgb(21, 69, 230);

   }
   button:hover{
        background:rgb(118, 147, 240);
   }
   button:active{
        background:rgb(195, 209, 255);
        color:black;
   }
   .passgen{
       padding:5px 5px;
       max-width:500px;
       font-family: 'Josefin Sans', sans-serif;
 
   }
   .errors{
        font-weight: bold;
        font-size:17px;
        color: #d91b42;
        margin:10px;
   }
  
   :global(body.dark) input{
        background-color: rgb(95, 95, 95);
        color: rgb(167, 167, 167);
       border: 1px solid black;
    }
    :global(body.dark) select{
        background-color: rgb(95, 95, 95);
        color: rgb(167, 167, 167);
       border: 1px solid black;
    }
 
    
</style>