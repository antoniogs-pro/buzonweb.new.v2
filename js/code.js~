var t, actual;

function select(i){
   actual = i;

  $("nav a")
    .removeClass("on off")
    .addClass(function(j){return(j===i)?"on":"off";});

  $("#descripcion").html(galeria[i].descripcion);
  $("#app").html(galeria[i].app);
  $("#imagen").attr("src", galeria[i].imagen);

  clearTimeout(t);
  t = setTimeout( function(){select((i + 1) % galeria.length);}, 2000);
}

function generar_selector(){ // regenera la botonera
  var selector = $("#selector");

  selector.html("");
  
  galeria.forEach(function(elem,i) {
    selector.append("<li><a onClick='select("+i+")'></a></li>");
  });
}

function borrar(elemento) { galeria.splice(elemento,1);}
function agregar() {
    actual = galeria.push({
       descripcion:$("#descripcion_d").html(),
       app:$("#app_d").html(),
       imagen:$("#imagen_d").html()
    }) - 1;
	return actual
}

$(function (){
  generar_selector();

  $("#editar").on("click", function(){
    clearTimeout(t);
    
    $("#descripcion_d").html(galeria[actual].descripcion);
    $("#app_d").html(galeria[actual].app);
    $("#imagen_d").html(galeria[actual].imagen);

    $("#datos").css("display", "block");
  })
// No editar
  $("#editar").on("dblclick", function(){
    clearTimeout(t);
     $("#datos").css("display", "none");
    generar_selector();
    select(actual);
  })
 // Cancelar editar
  $("#volver").on("click", function(){
    clearTimeout(t);
     $("#datos").css("display", "none");
    generar_selector();
    select(actual);
  }) 
// nuevo
  $("#nuevo").on("click", function(){
    $("#datos").css("display", "none");
    actual=agregar();
    generar_selector();
    select(actual);
  })
//modificar
$("#guardar").on("click", function(){
    $("#datos").css("display", "none");
    borrar(actual);
	actual=agregar();
    generar_selector();
    select(actual);
  })  
// borrar
  $("#borrar").on("click", function(){
    $("#datos").css("display", "none");
	borrar(actual);
    generar_selector();
    select(0);
  })

  select(0);
});
