Repositorio
===========

Repositorio de tareas
<!DOCTYPE html>
<!--
To change this license header, choose License Headers in Project Properties.
To change this template file, choose Tools | Templates
and open the template in the editor.
-->
<html lang="es">
    <head>
    <meta charset="utf-8" />
     <a style="color:#B4045F">
    <title>VerificarCédula</title>
     <body style="background:#F2F5A9">
    <h1><center>VALIDACIÓN DE NÚMERO DE CÉDULA, NÚMEROS PRIMOS Y NÚMEROS HEXADECIMALES</center></h1>
    </head>
    <form id="frmdata" name="frmdata"/>
    <a style="color:#0404B4">
        
        <b> Cedula:<input type="text" name="cedula"  id="cedula"/> </b>
    <input type="button" id="botonValidar" name="botonValidar"  value="VerificarCedula" onclick="ValidarCedula(document.forms[0].cedula.value)" />
    </form>
     <div id="idconcontenido">
            </div>
    <b <label>NumeroPrimo:</label>  <input type="text" id="txtpractica" value="" />  </b>
         <input type="button" id="BotonUno" value="ComprobarNumeroPrimo" onclick="numerosPrimos()" ></br> 
    
     <a style="color:#2E2E2E">
     </body>     
</html>
    <script>
        
        function ValidarCedula( form )
        {
        var cedula = form;
            arrayCedula = cedula.split( "" );
            var num = arrayCedula.length;
           
            if ( num == 10 )
            {
                
                var totalPosicionImpar=0;
                var UltimoDigito = (arrayCedula[9]);
                var totalPosicionPar = 0;
               
                for( i=0; i < (num-1); i++ )
                {
                  var mult = 0;
                  if ( ( i%2 ) != 0 ) { 
                    
                    var totalPosicionPar = totalPosicionPar + ( arrayCedula[i] *1); 
                    
                  }
                  else // Las posiciones impares , se multiplican *2 y las pares por 1
                  {
                    mult = arrayCedula[i] * 2;
                    
                        if ( mult > 9 ){ //si la multiplicación de las posiciones impares es igual o mayor a 9, se resta 9
                          totalPosicionImpar = parseInt(totalPosicionImpar + ( mult - 9 ));
                         
                        }else{
                            totalPosicionImpar = parseInt(totalPosicionImpar + mult);
                        }
                  }
                 
                }
                var Total= parseInt(totalPosicionPar + totalPosicionImpar);
                decena = Total / 10;
                decena = Math.floor( decena );
                decena = ( decena+1  ) * 10;
                decimo = ( decena - Total );
                if ( ( decimo == 10 && UltimoDigito == 0 ) || ( decimo == UltimoDigito ) ) {
                  alert( "LA CEDULA ES CORRECTA" );
                  return true;
                }
                else
                {
                  if(decimo==10)
                  {
                      decimo=0  // si el decimo digito es 10 se asume como cero
                      }
                  alert( "NUMERO DE CEDULA INCORRECTO, EL DECIMO DIGITO ES: " +decimo );
                  return false;
              }
                
            }
            else
            {
              alert("NUMERO DE CEDULA INCORRECT0");
              return false;
            }
          }
          
          function numerosPrimos()
   {
       var numero=document.getElementById("txtpractica").value
       var divisor=2
        var primo=true 
       
       while(divisor<numero)
        {
          if((numero%divisor)==0)  
          {
              primo=false
           
          }
          divisor ++
        }        
      alert(primo)
   }
</script>
