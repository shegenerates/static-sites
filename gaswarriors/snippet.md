# Snippet

```
<!-- Drop down -->
    <form name="gaswarriorform">
          <select class="numPick" name="numberPick" id="numberPick" form="gaswarriorform">
          <option value="1">1 Gas Warrior</option>
           <option value="2">2 Gas Warriors</option>
          <option value="3">3 Gas Warriors</option>
          <option value="4">4 Gas Warriors</option>
            <option value="5">5 Gas Warriors</option>
            <option value="6">6 Gas Warriors</option>
            <option value="7">7 Gas Warriors</option>
            <option value="8">8 Gas Warriors</option>
            <option value="9">9 Gas Warriors</option>
            <option value="10">10 Gas Warriors</option>
            <option value="11">11 Gas Warriors</option>
            <option value="12">12 Gas Warriors</option>
            <option value="13">13 Gas Warriors</option>
            <option value="14">14 Gas Warriors</option>
            <option value="15">15 Gas Warriors</option>
          </select>
        </form>
        <br>
        <iframe id="minterIframe"
          width="400"
          height="500"
          src="https://beta.oneclickdapp.com/embed/aurora-include?method=mint&arguments=1,80000000000000000"
          frameborder="0"
        ></iframe>

    <script src="https://code.jquery.com/jquery-3.6.0.slim.min.js" integrity="sha256-u7e5khyithlIdTpu22PHhENmPcRdFiHRjhAuHcs05RI=" crossorigin="anonymous"></script>
    <script>
    $("#numberPick").on('change',function(){
          var value=$(this).val();
          var wei = value*80000000000000000

          var linkStr = "https://beta.oneclickdapp.com/embed/aurora-include?method=mint&arguments=" + value + "," + wei
          $("#minterIframe").attr('src',linkStr);
      });

  </script>

<style>
      .numPick{
      font-family: inherit;
      font-size: 100%;
      background: #FFFFFF;
      border: 1px solid #000000;
      box-sizing: border-box;
      border-radius: 4px;
      padding: 0.5rem 1rem;
      transition: 500ms;
      }
</style>
```
