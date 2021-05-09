# preencher-dados

<div id="app"></div>

<div id="app"></div>

<div id="app"></div>

Esse script, retirei o javascript do calendario e as class para ficar menor
<html>
<head>
<meta http-equiv="content-type" content="text/html; charset=ISO-8859-1">

<?php

$UserName = 'soares';

mysql_connect ("localhost", "root", "soares");
mysql_select_db("boleto");

$sql = mysql_query("SELECT * FROM cadastro where UserName = '$UserName'") or die("cliente_nao_encontrado".mysql_error());

while ($num = mysql_fetch_array($sql)) {

?>

<title>Gera Boleto - Proserv</title>
</head><body onmouseup="ShowPrintPopup(event,'Imprimir esta página');" bgcolor="#ffffff">

<center>

<form method="POST" action="boleto_cef.php" name="boleto">
<table style="border-collapse: collapse;" border="1" bordercolor="#111111" cellpadding="0" cellspacing="0" width="100%">
<tbody><tr>
<td valign="top" width="100%">
<table border="0" cellpadding="4" cellspacing="4" width="100%">
<tbody><tr>
<td colspan="4" bgcolor="#68b6b7"><font face="Arial" size="2"><b>Gera Boleto</b></font><b></b></td>
</tr><tr>
<td bgcolor="#e9e9e9" width="150"><font face="Arial" size="2">C&oacute;digodo Cliente:<font color="#ff0000">*</font></font></td>
<td width="159" colspan="1" bgcolor="#e9e9e9"><input name="id_cliente" id="id_cliente" size="10" value="<?php echo $num['ID'];?>" type="text"></td>
<td bgcolor="#e9e9e9" width="154"><font face="Arial" size="2">N.&ordm; Documento:<font color="#ff0000">*</font></font></td>
<td width="439" bgcolor="#e9e9e9"><input name="numero_documento" id="numero_documento" size="15" value="<?php echo date('dy');?>" type="text"></td>
</tr><tr>
<td bgcolor="#e9e9e9" ><font face="Arial" size="2">Nome Cliente:<font color="#ff0000">*</font></font></td>
<td bgcolor="#e9e9e9" colspan="3"><input name="nome" size="50" value="<?php echo $num['nome'];?>" type="text" id="nome"> </td></tr><tr>
<td bgcolor="#e9e9e9" width="150"><font face="Arial" size="2">Valor do Boleto:<font color="#ff0000">*</font></font></td>
<td colspan="3" bgcolor="#e9e9e9"><input name="valor" value="" type="text"></td>
</tr><tr>
<td bgcolor="#e9e9e9"><font face="Arial" size="2">Data de Emis&atilde;o:<font color="#ff0000">*</font></font></td>
<td colspan="6" bgcolor="#e9e9e9"><input name="date_ini" size="12" type="text">

<a href="javascript:%20calendar1.show()"></a>
<div style="visibility: hidden;" class="dynCalendar" id="dynCalendar_layer_0" onMouseOver="calendar1._mouseover(true)" onMouseOut="calendar1._mouseover(false)"></div></td>
</tr><tr>
<td bgcolor="#e9e9e9"><font face="Arial" size="2">Dia do Vencimento:<font color="#ff0000">*</font></font></td>
<td colspan="6" bgcolor="#e9e9e9"><input name="date_cto_ini" id="date_cto_ini" size="12" type="text">
<a href="javascript:%20calendar2.show()"></a><div style="visibility: hidden;" class="dynCalendar" id="dynCalendar_layer_0" onMouseOver="calendar2._mouseover(true)" onMouseOut="calendar2._mouseover(false)"></div></td>
</tr>
<tr>
<td bgcolor="#e9e9e9" width="150"><font face="Arial" size="2">Endere&ccedil;o:<font color="#ff0000">*</font> </font></td>
<td bgcolor="#e9e9e9" colspan="3"><input name="endereco" size="50" value="<?php echo $num['endereco'];?>" type="text"></td>
</tr><tr>

<td bgcolor="#e9e9e9" width="150">Bairro:<font face="Arial" size="2"><font color="#ff0000">*</font></font></td>
<td bgcolor="#e9e9e9" colspan="3"><input name="bairro" value="<?php echo $num['bairro'];?>" type="text"></td>
</tr>
<tr>
<td bgcolor="#e9e9e9">Cep:<font face="Arial" size="2"><font color="#ff0000">*</font></font></td>
<td bgcolor="#e9e9e9" colspan="3"><input name="cep" value="<?php echo $num['cep'];?>" type="text"></td>
</tr>
<tr>
<td bgcolor="#e9e9e9">&nbsp;</td>
<td bgcolor="#e9e9e9" colspan="3">&nbsp;</td>
</tr>
<tr>
</tbody></table>
</td>
</tr>
</tbody></table>
<br>
<table width="100%">
<tbody><tr>
<td colspan="6" align="right">
<input type="reset" name="Submit2" class="button" value="Limpar">
<input type="submit" name="Submit" class="button" value="Enviar">
</td>
</tr>
</tbody></table>

</form>

</center>


<form id="cad" method="post" action="#" required>
    <h3>Dados pessoais</h3>
    Nome: <input type="text" name="txtnome" maxlength="40" required />
    <br>
    Sobrenome: <input type="text" name="txtsobrenome" maxlength="30" required />
    <br>
    Data de nascimento: <input type="date" name="txtdata_nasc" required />
    <br>
    CPF: <input type="text" id="cpf1" name="txtCPF" maxlength="11" required />
    <br>

    <h3>Dados para Contato</h3>
    DDD: <input type="text" name="txtDDD" placeholder="Ex: (###)"  maxlength="2" required /><br>
    Tipo: <input type="radio" name="rbT" value="Celular" checked />Celular
    <input type="radio" name="rbT" value="Telefone" />Telefone
    <br>  
    Nº: <input type="tel" name="txtContato" maxlength="9" required  />
    <br>  
    E-mail: <input type="email" name="txtEmail1" maxlength="50" id="Email1" placeholder="nome@email.com" required />
    <br>
    Confirmação de E-mail: <input type="email" name="txtEmail2" maxlength="50" id="Email2" required />
    <br>

    <h3>Dados do Endereço</h3>
    Logradouro: <input type="text" name="txtRua" maxlength="50" required />
    <br>
    Bairro: <input type="text" name="txtBairro" maxlength="35" required />
    <br>
    Cidade: <input type="text" name="txtCidade" maxlength="25" required />
    <br>
    Estado:
    <select name="cbEstado" required>
        <option>Acre</option>    
        <option>Alagoas</option>
        <option>Amapá</option>
        <option>Amazonas</option>
        <option>Bahia</option>
        <option>Brasília</option>
        <option>Ceará</option>
        <option>Espírito Santo</option>
        <option>Goiás</option>
        <option>Maranhão</option>
        <option>Mato Grosso</option>
        <option>Mato Grosso do Sul</option>
        <option>Minas Gerais</option>
        <option>Pará</option>
        <option>Paraíba</option>
        <option>Paraná</option>
        <option>Pernambuco</option>
        <option>Piauí</option>
        <option>Rio de Janeiro</option>
        <option>Rio Grande do Norte</option>
        <option>Rio Grande do Sul</option>
        <option>Rondônia</option>
        <option>Roraima</option>
        <option>Santa Catarina</option>
        <option>São Paulo</option>
        <option>Sergipe</option>
        <option>Tocantins</option>
    </select>
    <br>
    Número: <input type="text" name="txtNumero" maxlength="7" required />
    <br>
    CEP: <input type="text" name="txtCep" placeholder="Ex: #####-###" maxlength="8" required />
    <br>
    Complemento: <input type="text" name="txtComplemento" maxlength="40" />
    <br>

    <h3>Dados da conta</h3>
    Nome de usuário: <input type="text" name="txtLogin" required maxlength="20" />
    <br>
    Senha: <input type="password" name="txtsenha" required maxlength="20" />
    <br>
    Confirmação da senha: <input type="password" name="txtCsenha" required maxlength="20" />
    <br>
    Tipo de usuário: <input type="radio" name="rb" value="Usuario" checked />Cliente
    <input type="radio" name="rb" value="Tecnico" />Técnico
    <br>

    <button type="button" id="btn1" onclick='javascript: validarFormulario()'>Cadastrar</button>
</form>


  <td colspan="3" align="center"><input type="submit" name="Enviar" value="Enviar " />
        <input type="reset" name="Limpar" value="Limpar" /></td>
   <!-- Área -->
                <!--Painel de Cadastro -->
        <section class="cadastro">
            <article class="cadastro_area">
                <header>
                    <h2 class="descricao">Verificação de campos iguais com HTML5 e Javascript</h2>
                </header>
                <form id="formCadastro" name="formulario" action="" method="POST">
                    <label for="txtSenha">Senha</label>
                    <input id="txtSenha" name="senha" type="password" required placeholder="Digite uma Senha" title="Senha" />
                    <label for="repetir_senha">Confirmar Senha</label>
                    <input id="repetir_senha" name="repetir_senha" type="password" required  placeholder="Repetir Senha" title="Repetir Senha" oninput="validaSenha(this)" />
                    <button type="submit" class="testar">Testar</button>

                    
             <form name="form1" method="post" action="enviar_contato.php" >
  <p> </p>
  <table width="386" border="0" class="cadastro">
  <tr>
    <td class="cadastro"><table width="386" border="0" class="cadastro">
      <tr>
        <td colspan="2">Nome: </td>
        <td width="8"><font color="#FF0000">*</font></td>
        <td width="235"><input name="nome" type="text" id="nome" size="50"></td>
      </tr>
      <tr>
        <td colspan="2">Sobrenome: </td>
        <td><font color="#FF0000">*</font></td>
        <td><input name="sobrenome" type="text" id="sobrenome" size="50"></td>
      </tr>
      <tr>
        <td colspan="2">Empresa: </td>
        <td> </td>
        <td><input name="empresa" type="text" id="empresa" size="50"></td>
      </tr>
      <tr>
        <td colspan="2">Telefone: </td>
        <td><font color="#FF0000">*</font></td>
        <td><input name="ddd" type="text" id="ddd" size="2" maxlength="2">
          <input name="telefone" type="text" id="telefone" size="8" maxlength="8"></td>
      </tr>
      <tr>
        <td colspan="2">Email:</td>
        <td><font color="#FF0000">*</font></td>
        <td><input name="email" type="text" id="email" size="50"></td>
      </tr>
      <tr>
        <td colspan="2">Cidade: </td>
        <td><font color="#FF0000">*</font></td>
        <td><input name="cidade" type="text" id="cidade" size="50"></td>
      </tr>
      <tr>
        <td colspan="2">Estado: </td>
        <td><font color="#FF0000">*</font></td>
        <td class="cadastro">
        <select name="estado" class="cadastro" id="estado">
          <option selected value="">Escolha um Estado...</option>
          <option value="acre" >Acre</option>
          <option value="alagoas">Alagoas</option>
          <option value="amapá">Amapá</option>
          <option value="amazonas">Amazonas</option>
          <option value="bahia">Bahia</option>
          <option value="ceara">Ceará</option>
          <option value="DF">Distrito Federal</option>
          <option value="ES">Espírito Santo</option>
          <option value="goias">Goiás</option>
          <option value="maranhao">Maranhão</option>
          <option value="mato grosso">Mato Grosso</option>
          <option value="mato grosso do sul">Mato Grosso do Sul</option>
          <option value="minas gerais">Minas Gerais</option>
          <option value="para">Pará</option>
          <option value="paraiba">Paraíba</option>
          <option value="parana">Paraná</option>
          <option value="pernambuca">Pernambuco</option>
          <option value="piaui">Piauí</option>
          <option value="rio de janeiro">Rio de Janeiro</option>
          <option value="rio grande do norte">Rio Grande do Norte</option>
          <option value="rio grande do sul">Rio Grande do Sul</option>
          <option value="rondonia">Rondônia</option>
          <option value="roraima">Roraima</option>
          <option value="santa catarina">Santa Catarina</option>
          <option value="sao paulo">São Paulo</option>
          <option value="sergipe">Sergipe</option>
          <option value="tocantins">Tocantins</option>
        </select></td>
      </tr>
      <tr>
        <td colspan="2"><p>Categoria:</p></td>
        <td><font color="#FF0000">*</font></td>
        <td><select name="categoria" id="categoria">
          <option>Escolha uma Categoria</option>
          <option>Consumidor</option>
          <option>Distribuidor</option>
          <option>Representante</option>
        </select></td>
      </tr>
      <tr>
        <td colspan="2"> </td>
        <td> </td>
        <td> </td>
      </tr>
      <tr>
        <td colspan="4"> Mensagem<br>
          <textarea name="mensagem" cols="50%" rows="5" wrap="VIRTUAL" id="mensagem"></textarea>
          <br>
          <br></td>
      </tr>
      <tr>
        <td colspan="4"></td>
      </tr>
      <tr>
        <td colspan="4"><p>
          <input name="news" type=checkbox value=sim checked>
          Quero me cadastrar para receber novidades por e-mail.<br>
          <br>
          <font color="#FF0000" size="2"> *preenchimento obrigatório </font> <br>
        </p></td>
      </tr>
      <tr>
        <td width="60"><input type="reset" name="Limpar" id="Limpar" value="Limpar"></td>
        <td width="56">  <input type="submit" name="Submit" value="Enviar" onClick="return valida()"></td>
        <td> </td>
        <td> </td>
      </tr>
    </table></td>
  </tr>
  </table>
        </form>
