<script language="JavaScript">
function contidoNasBases(Dados, Bases){
  var i, j;
  if (Dados == "") return false;
  for (i=0; i<Dados.length; i++){
    for (j=0; j<Bases.length; j++){
      if (Dados.substr(i,1) == Bases.substr(j,1)) break;
    }
    if (j >= Bases.length) return false;
  }
  return true;
}

function BaseParaDecimal(Base, Dado){
  var Dig, IExp=0, Saida=0, i, j;
  var Digs = "0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ";
  for(i=Dado.length-1; i>=0; i--){
    Dig = -1;
    for(j=0; j<Digs.length; j++){
      if(Dado.charAt(i) == Digs.charAt(j)){
        Dig = j;
        break;
      }
    }
    if(Dig >= 0){
      Saida += Dig * Math.pow(Base, IExp);
      IExp++;
    }
  }
  return Saida;
}

function DecimalParaBase(Base, Dado){
  var Valor=Dado, Numero=0, Div, IDiv, Saida="", i;
  var Digs = "0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ"
  while(Valor >= 1){
    Valor = Valor / Base;
    Numero++;
  }
  Valor = Dado;
  if(Numero == 0) Numero = 1;
  for(i=Numero-1; i>=0; i--){
    Div = Math.pow(Base, i);
    IDiv = Math.floor(Valor / Div);
    Saida += Digs.charAt(IDiv);
    Valor -= Div * IDiv;
  }
  return Saida;
}

function SelConverter(){
  var f = document.form;
  var BaseEntrada = f.BaseEntrada[f.BaseEntrada.selectedIndex].value;
  var BaseSaida = f.BaseSaida[f.BaseSaida.selectedIndex].value
  var Bases = " 0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ";
  var Valor = f.ValIn.value;
  var DomBase;
  if (BaseEntrada == ""){
    alert("É necessário informar a Base de Entrada.");
    f.BaseEntrada.focus();
    return;
  }
  if (Valor == ""){
    alert("É necessário informar o Valor de Entrada.");
    f.ValIn.focus();
    return;
  }
  DomBase = Bases.substr(0, parseInt(BaseEntrada) + 1);
  if (!contidoNasBases(Valor, DomBase)){
    alert("O Valor de Entrada deve conter somente caracteres do Domínio das bases '" + DomBase + "'.");
    f.ValIn.focus();
    return;
  }
  if (BaseSaida == ""){
    alert("É necessário informar a Base de Saí­da.");
    f.BaseSaida.focus();
    return;
  }
  if (parseInt(BaseEntrada) != 10){
    Valor = BaseParaDecimal(BaseEntrada, Valor);
  }
  if (parseInt(BaseSaida) != 10){
    Valor = DecimalParaBase(BaseSaida, Valor);
  }
  f.ValOut.value = Valor;
}
</script>

<p>
  <font size="6" face="Gilroy">
  Conversor De Bases Numéricas De Binário até Z
  </font>
  </p>

<form name="form">
  <b>Valor de Entrada:</b><input size=19 type="text" name="ValIn"><br>   
  <b>Base de Entrada:</b>
    <select name="BaseEntrada">
      <option value=""></option>
      <option value='2'>2 (0 ~ 1) - binário</option>
      <option value='3'>3 (0 ~ 2)</option>
      <option value='4'>4 (0 ~ 3)</option>
      <option value='5'>5 (0 ~ 4)</option>
      <option value='6'>6 (0 ~ 5)</option>
      <option value='7'>7 (0 ~ 6)</option>
      <option value='8'>8 (0 ~ 7) - octal</option>
      <option value='9'>9 (0 ~ 8)</option>
      <option value='10'>10 (0 ~ 9) - decimal</option>
      <option value='11'>11 (0 ~ A)</option>
      <option value='12'>12 (0 ~ B)</option>
      <option value='13'>13 (0 ~ C)</option>
      <option value='14'>14 (0 ~ D)</option>
      <option value='15'>15 (0 ~ E)</option>
      <option value='16'>16 (0 ~ F) - hexadecimal</option>
      <option value='17'>17 (0 ~ G)</option>
      <option value='18'>18 (0 ~ H)</option>
      <option value='19'>19 (0 ~ I)</option>
      <option value='20'>20 (0 ~ J)</option>
      <option value='21'>21 (0 ~ K)</option>
      <option value='22'>22 (0 ~ L)</option>
      <option value='23'>23 (0 ~ M)</option>
      <option value='24'>24 (0 ~ N)</option>
      <option value='25'>25 (0 ~ O)</option>
      <option value='26'>26 (0 ~ P)</option>
      <option value='27'>27 (0 ~ Q)</option>
      <option value='28'>28 (0 ~ R)</option>
      <option value='29'>29 (0 ~ S)</option>
      <option value='30'>30 (0 ~ T)</option>
      <option value='31'>31 (0 ~ U)</option>
      <option value='32'>32 (0 ~ V)</option>
      <option value='33'>33 (0 ~ W)</option>
      <option value='34'>34 (0 ~ X)</option>
      <option value='35'>35 (0 ~ Y)</option>
      <option value='36'>36 (0 ~ Z)</option>
    </select><br>
  <b>Base de Saída:</b>
    <select name="BaseSaida">
      <option value=""></option>
      <option value='2'>2 (0 ~ 1) - binário</option>
      <option value='3'>3 (0 ~ 2)</option>
      <option value='4'>4 (0 ~ 3)</option>
      <option value='5'>5 (0 ~ 4)</option>
      <option value='6'>6 (0 ~ 5)</option>
      <option value='7'>7 (0 ~ 6)</option>
      <option value='8'>8 (0 ~ 7) - octal</option>
      <option value='9'>9 (0 ~ 8)</option>
      <option value='10'>10 (0 ~ 9) - decimal</option>
      <option value='11'>11 (0 ~ A)</option>
      <option value='12'>12 (0 ~ B)</option>
      <option value='13'>13 (0 ~ C)</option>
      <option value='14'>14 (0 ~ D)</option>
      <option value='15'>15 (0 ~ E)</option>
      <option value='16'>16 (0 ~ F) - hexadecimal</option>
      <option value='17'>17 (0 ~ G)</option>
      <option value='18'>18 (0 ~ H)</option>
      <option value='19'>19 (0 ~ I)</option>
      <option value='20'>20 (0 ~ J)</option>
      <option value='21'>21 (0 ~ K)</option>
      <option value='22'>22 (0 ~ L)</option>
      <option value='23'>23 (0 ~ M)</option>
      <option value='24'>24 (0 ~ N)</option>
      <option value='25'>25 (0 ~ O)</option>
      <option value='26'>26 (0 ~ P)</option>
      <option value='27'>27 (0 ~ Q)</option>
      <option value='28'>28 (0 ~ R)</option>
      <option value='29'>29 (0 ~ S)</option>
      <option value='30'>30 (0 ~ T)</option>
      <option value='31'>31 (0 ~ U)</option>
      <option value='32'>32 (0 ~ V)</option>
      <option value='33'>33 (0 ~ W)</option>
      <option value='34'>34 (0 ~ X)</option>
      <option value='35'>35 (0 ~ Y)</option>
      <option value='36'>36 (0 ~ Z)</option>
    </select>  <br>
  <b>Valor de Saída:</b><input type="text" name="ValOut">  <br>
  <br>
  <input type="button" value="Converter" OnClick="SelConverter()">
  
</form>
