import json
import re 
import datetime as dt


db=[]
#SE ASIGNA LA LISTA PRINCIPAL
clientes={}
productos={}
facturas={}
detelles={}
#SE ASIGNAN LOS DICCIONARIOS QUE IRAN DENTRO DE LA LISTA DB

productos[1]=["CLORALEX",85.00,40.00,0.16]
productos[2]=["ESCOBA PLUS",125.00, 55.00,0.16]
productos[3]=['TOMATE HUAJE',45.00,28.00,0.0]



clientes[1]=['JUAN PÉREZ', 'Juárez #100', dt.datetime(2022,10,1)]
facturas[1]=[dt.datetime.strftime(dt.datetime.now(),"%D"), 1,
             {
                1:[1, 2, 85.00, 40.00,0.16],
                2:[3,5,45.00,28.00,0.0]
             }
             ]



db=[productos, clientes, facturas]

def regular_input(regex,mensaje_input,mensaje_re):
  while True:
    data=input(mensaje_input)
    if data =="":
      print("ERROR. EL CAMPO NO DEBE DE OMITIRSE. INGRESE DE NUEVO")
      continue
    if not (bool(re.match(regex,data))):
      print(mensaje_re)
      continue  
    break  
  return data

def CRUD_P():
      global productos #Llamamos a las variables globales
      while True: #Declaramos un ciclo infinito
        #Preguntamos el identificador del producto.
        id_producto=regular_input("^([0-9])+|([r,R])$", "DIGITE EL ID DEL PRODUCTO  O [R]egresar:", "ERROR, NO INGRESO UN VALOR DE ACUERDO A LO REQUERIDO, INTENTE DE NUEVO ")
        #Siel usuario quiere regresar rompemos el ciclo infinito
        if id_producto.upper() == "R":
          break
       #Cambiamos la variable a tipo entero para identificar si la llave existe o existente
        _id_producto=int(id_producto)
        if _id_producto in productos.keys():#verifica que el id digitado por el usuario este en nuestras credenciales
          print(f"su producto es {productos[_id_producto][0]} \nSU PRECIO ES DE:{productos[_id_producto][1]} \nSU COSTO ES DE: {productos[_id_producto][2]} \nSU IVA ES DE: {productos[_id_producto][3]}")#damos la informacione del producto
          opcion_mod=regular_input("^([E,M,R,e,m,r]{0,1}$)","QUE QUIERES HACER [E]LIMINAR [M]ODIFICAR [R]EGRESAR\n ", "ERROR, LA OPCION DIGITA NO SE ENCUENTRA EN LAS OPCIONES DISPONIBLES \nINTENTE DE NUEVO")
          if opcion_mod.upper()=="E":#elimina el producto de nuestro diccionario
            del productos[_id_producto]
            print("Su movimiento fue generado exitosamentes")
          elif opcion_mod.upper()=="M":#entra a la pestaña de modificar
          #preguntamos el dato no primo a modificar 
            mod_producto=regular_input("^([D,P,C,I,d,p,c,i]{0,1})$","DESEA MODIFICAR LA DESCIPCION DEL PRODUCTO [S]I [N]O?" , "ERROR, LA OPCION DIGITA NO SE ENCUENTRA EN LAS OPCIONES DISPONIBLES \nINTENTE DE NUEVO")
            if mod_producto.upper()=="S": #MODIFICACION DE LA DESCRIPCION
              desc_producto=regular_input("^([a-z, ,A-Z]{0,256})$","A CONTINUACION MODIFICACARAS LA DESCRIPCION DEL PRODUCTO \nTIENES 256 CARACTERES","EXCEDIO EL NUMERO DE CARACTERES EN LA DESCRIPCION INTENTE DE NUEVO")
              productos[_id_producto][0]=desc_producto
              print("Su movimiento ha sido generado existosamente")

            mod_producto=regular_input("^([D,P,C,I,d,p,c,i]{0,1})$","DESEA MODIFICAR EL PRECIO DEL PRODUCTO [S]I [N]O?" , "ERROR, LA OPCION DIGITA NO SE ENCUENTRA EN LAS OPCIONES DISPONIBLES \nINTENTE DE NUEVO")
            if mod_producto.upper()=="S": #MODIFICACION DEL PRECIO
              price_producto=regular_input("^([0-9]{0,6}|[0-9]{0,6}[.][0-9]{0,2})$","A CONTINUACION MODIFICACARAS EL PRECIO \nTIENE EL PATRON 999,999.00 ","ERROR, EXCEDIO EL PATRON DE 999,999.00 INTENTE DE NUEVO")
              _price_producto=float(price_producto)
              productos[_id_producto][1]=_price_producto
              print("Su movimiento ha sido generado existosamente")

            mod_producto=regular_input("^([D,P,C,I,d,p,c,i]{0,1})$","DESEA MODIFICAR EL COSTO DEL PRODUCTO [S]I [N]O?" , "ERROR, LA OPCION DIGITA NO SE ENCUENTRA EN LAS OPCIONES DISPONIBLES \nINTENTE DE NUEVO")
            if mod_producto.upper()=="S": #MODIFICACION DEL COSTO
              cost_producto=regular_input("^([0-9]{0,6}|[0-9]{0,6}[.][0-9]{0,2})$","A CONTINUACION MODIFICACARAS EL COSTO \nTIENE EL PATRON 999,999.00 ","ERROR, EXCEDIO EL PATRON DE 999,999.00 INTENTE DE NUEVO")
              _cost_producto=float(cost_producto)
              productos[_id_producto][2]=_cost_producto
              print("Su movimiento ha sido generado existosamente")

            mod_producto=regular_input("^([D,P,C,I,d,p,c,i]{0,1})$","DESEA MODIFICAR LA TASA DE IMPUESTO DEL PRODUCTO [S]I [N]O?" , "ERROR, LA OPCION DIGITA NO SE ENCUENTRA EN LAS OPCIONES DISPONIBLES \nINTENTE DE NUEVO")
            if mod_producto.upper()=="S": #MODIFICACiON DEL IMPUESTO
              impuesto_producto=regular_input("^([0-9]{0,6}|[0-9]{0,6}[.][0-9]{0,2})$","A CONTINUACION MODIFICACARAS EL IMPUESTO \nTIENE EL PATRON 999,999.00 ","ERROR, EXCEDIO EL PATRON DE 999,999.00 INTENTE DE NUEVO")
              _impuesto_producto=float(cost_producto)
              productos[_id_producto][2]=_impuesto_producto
              print("Su movimiento ha sido generado existosamente")


        else:
          #si el id no existe preguntara si queremos crear un registro con ese identificador
            create_opcion = regular_input("^([C,c,r,R])$","EL IDENTIFICADOR QUE USTED PROPORCIONO NO SE ENCUENTRA EN NUESTROS DESEA: [C]CREARLO  O [R]EGRESAR","EL PARTRON NO ES EL CORRECTO")
            if create_opcion.upper() == "C":
              lista_atributos = []
              #Creacion de atributo DESCRIPCION DEL PRODUCTO
              desc_producto=regular_input("^([a-z, ,A-Z]{0,256})$","ESCRIBE EL NOMBRE DEL PRODUCTO \nTIENES 256 CARACTERES","EXCEDIO EL NUMERO DE CARACTERES EN LA DESCRIPCION INTENTE DE NUEVO")
              lista_atributos.append(desc_producto)
              #Creacion de atributo PRECIO
              price_producto=regular_input("^([0-9]{0,6}|[0-9]{0,6}[.][0-9]{0,2})$","A CONTINUACION LE PONDRAS  EL PRECIO \nTIENE EL PATRON 999,999.00 ","ERROR, EXCEDIO EL PATRON DE 999,999.00 INTENTE DE NUEVO")
              lista_atributos.append(float(price_producto))
              #Creacion de atributo COSTO
              cost_producto=regular_input("^([0-9]{0,6}|[0-9]{0,6}[.][0-9]{0,2})$","A CONTINUACION DIGITARAS EL COSTO \nTIENE EL PATRON 999,999.00 ","ERROR, EXCEDIO EL PATRON DE 999,999.00 INTENTE DE NUEVO")
              lista_atributos.append(float(cost_producto))  
              #Creacion de atributo IMPUESTO
              impuesto_producto=regular_input("^([0-9]{0,6}|[0-9]{0,6}[.][0-9]{0,2})$","A CONTINUACION DIGITARAS LA TASA DE IMPUESTO \nTIENE EL PATRON 999,999.00 ","ERROR, EXCEDIO EL PATRON DE 999,999.00 INTENTE DE NUEVO")
              lista_atributos.append(float(impuesto_producto))

              #se rellenan los campos en el orden correspondientey se agrega al diccionario
              productos[_id_producto]=lista_atributos
              print("TU MOVIMIENTO SE GENERO EXITOSAMENTE")
        
def CRUD_c():
      global clientes #Llamamos a las variables globales
      while True: #Declaramos un ciclo infinito
        id_cliente=regular_input("^([0-9])+|([r,R])$", "DIGITE EL ID DEL CLIENTE  O [R]egresar:", "ERROR, NO INGRESO UN VALOR DE ACUERDO A LO REQUERIDO, INTENTE DE NUEVO ")
        if id_cliente.upper() == "R":
          break
        _id_cliente=int(id_cliente)
        if _id_cliente in clientes.keys():#verifica que el id digitado por el usuario este en nuestras credenciales
          print(f"usted es {clientes[_id_cliente][0]} \nVIVE EN :{clientes[_id_cliente][1]} \nSU REGISTRO SE LLEVO A CABO EL: {clientes[_id_cliente][2]} \n")#damos la informacione del USUARIO
          opcion_mod=regular_input("^([E,M,R,e,m,r]{0,1}$)","QUE QUIERES HACER [E]LIMINAR [M]ODIFICAR [R]EGRESAR\n ", "ERROR, LA OPCION DIGITA NO SE ENCUENTRA EN LAS OPCIONES DISPONIBLES \nINTENTE DE NUEVO")
          if opcion_mod.upper()=="E":#elimina el producto de nuestro diccionario
            del clientes[_id_cliente]
            print("Su movimiento fue generado exitosamente")
          elif opcion_mod.upper()=="M":#entra a la pestaña de modificar
          
            mod_cliente=regular_input("^([S,s,N,n]{0,1})$","DESEA MODIFICAR EL NOMBRE DEL CLIENTE [S]I [N]O?" , "ERROR, LA OPCION DIGITA NO SE ENCUENTRA EN LAS OPCIONES DISPONIBLES \nINTENTE DE NUEVO")
            if mod_cliente.upper()=="S": #MODIFICACION DEL NOMBRE DEL COMPRADOR
              nombre_cliente=regular_input("^([a-z, ,A-Z]{0,256})$","A CONTINUACION MODIFICACARAS EL NOMBRE DEL CLIENTE \nTIENES 256 CARACTERES","EXCEDIO EL NUMERO DE CARACTERES EN LA DESCRIPCION INTENTE DE NUEVO")
              clientes[_id_cliente][0]=nombre_cliente
              print("Su movimiento ha sido generado existosamente")

            mod_cliente=regular_input("^([S,s,N,n]{0,1})$","DESEA MODIFICAR EL DOMICILIO DEL CLIENTE [S]I [N]O?" , "ERROR, LA OPCION DIGITA NO SE ENCUENTRA EN LAS OPCIONES DISPONIBLES \nINTENTE DE NUEVO")
            if mod_cliente.upper()=="S": #MODIFICACION DEL DOMICILIO
              domicilio=regular_input("^([a-z, ,A-Z]{0,256})$","A CONTINUACION MODIFICACARAS la direccion de tu domicilio \nTIENES UN LIMITE DE 256 CARACTERES ","ERROR, EXCEDIO EL LIMITE DE CARACTERES INTENTE DE NUEVO")
              clientes[_id_cliente][1]=domicilio
              print("Su movimiento ha sido generado existosamente")

            mod_cliente=regular_input("^([S,s,N,n]{0,1})$","DESEA MODIFICAR LA FECHA DE REGISTRO [S]I [N]O?" , "ERROR, LA OPCION DIGITA NO SE ENCUENTRA EN LAS OPCIONES DISPONIBLES \nINTENTE DE NUEVO")
            if mod_cliente.upper()=="S": #MODIFICACION DE LA FECHA DE REGISTRO
              fecha = dt.datetime.now()
              fecha = dt.datetime.strftime(fecha,"%D")
              clientes[_id_cliente][2]= fecha
              print("Su movimiento ha sido generado existosamente")

        else:
          #si el id no existe preguntara si queremos crear un registro con ese identificador
            create_opcion = regular_input("^([C,c,r,R])$","EL IDENTIFICADOR QUE USTED PROPORCIONO NO SE ENCUENTRA EN NUESTROS DESEA: [C]CREARLO  O [R]EGRESAR","EL PARTRON NO ES EL CORRECTO")
            if create_opcion.upper() == "C":
              lista_atributos = []
              #creacion de nombre
              nombre_cliente=regular_input("^([a-z, ,A-Z]{0,256})$","A CONTINUACION DIGITA EL NOMBRE DEL CLIENTE \nTIENES 256 CARACTERES","EXCEDIO EL NUMERO DE CARACTERES EN LA DESCRIPCION INTENTE DE NUEVO")
              lista_atributos.append(nombre_cliente)
              #creacion de domicilio
              domicilio=regular_input("^([a-z, ,A-Z]{0,256})$","DIGITE EL DOMICILIO DEL CLIENTE \nTIENES UN LIMITE DE 256 CARACTERES ","ERROR, EXCEDIO EL LIMITE DE CARACTERES INTENTE DE NUEVO")
              lista_atributos.append(domicilio)
              #fecga de registro
              fecha = dt.datetime.now()
              fecha = dt.datetime.strftime(fecha,"%D")
              lista_atributos.append(fecha)        

              #se rellenan los campos en el orden correspondientey se agrega al diccionario
              clientes[_id_cliente]=lista_atributos

def CRUD_FACTURAS():
  global clientes,productos,facturas
  while True:
    id_facturas=regular_input("^([0-9])+|([r,R])$", "DIGITE EL ID DE LA FACTURA  O [R]egresar:", "ERROR, NO INGRESO UN VALOR DE ACUERDO A LO REQUERIDO, INTENTE DE NUEVO ")
    if id_facturas.upper() == "R":
      break
    _id_facturas = int(id_facturas)
    if _id_facturas in clientes.keys():
      print(txt_facturas(_id_facturas))
      opcion_mod=regular_input("^([E,M,R,e,m,r]{0,1}$)","QUE QUIERES HACER [E]LIMINAR [M]ODIFICAR [R]EGRESAR\n ", "ERROR, LA OPCION DIGITA NO SE ENCUENTRA EN LAS OPCIONES DISPONIBLES \nINTENTE DE NUEVO")
      if opcion_mod.upper()=="E":#elimina el producto de nuestro diccionario
        del facturas[_id_facturas]
        print("Su movimiento fue generado exitosamentes")
      elif opcion_mod.upper()=="M":#entra a la pestaña de modificar

        mod_cliente=regular_input("^([S,s,N,n]{0,1})$","DESEA MODIFICAR EL COMPRADOR QUE APARECE EN LA FACTURA [S]I [N]O?" , "ERROR, LA OPCION DIGITA NO SE ENCUENTRA EN LAS OPCIONES DISPONIBLES \nINTENTE DE NUEVO")
        if mod_cliente.upper()=="S": #MODIFICACION DE EL ID DEL CLIENTE SE VALIDA QUE ESTE ESTE PREVIAMENTE REGISTRADO
          while True:
            _id_cliente=regular_input("^([0-9])+$","DIGITE EL ID DEL COMPRADOR \nTIENES UN LIMITE DE 256 CARACTERES ","EL IDENTIFICADOR NO CUMPLE CON EL PATRON")
            id_cliente = int(_id_cliente)                          
            if not(id_cliente in clientes.keys()):
              print("ese id no existe")
              continue
            facturas[_id_facturas][1]= id_cliente
            print("Su movimiento ha sido generado existosamente")
            break

        mod_cliente=regular_input("^([S,s,N,n]{0,1})$","DESEA MODIFICAR LA FECHA DE REGISTRO [S]I [N]O?" , "ERROR, LA OPCION DIGITA NO SE ENCUENTRA EN LAS OPCIONES DISPONIBLES \nINTENTE DE NUEVO")
        if mod_cliente.upper()=="S": #MODIFICACION DE LA FECHA A LA FECHA ACTUAL
          fecha = dt.datetime.now()
          fecha = dt.datetime.strftime(fecha,"%D")
          facturas[_id_facturas][0]= fecha
          print("Su movimiento ha sido generado existosamente")

        mod_cliente=regular_input("^([S,s,N,n]{0,1})$","DESEA MODIFICAR LAS PROPIEDADES DE LAS FACTURAS [S]I [N]O?" , "ERROR, LA OPCION DIGITA NO SE ENCUENTRA EN LAS OPCIONES DISPONIBLES \nINTENTE DE NUEVO")
        if mod_cliente.upper()=="S": #MODIFICACION DE LAS PROPIDADES DE LAS FACTURAS SE INICIA UN CICLO FOR PARA RECORRER EL DICCIONARIO
          for i in facturas[_id_facturas][2].keys():

            mod_cliente=regular_input("^([S,s,N,n]{0,1})$","DESEA MODIFICAR LA CANTIDAD DEL PRODUCTO ADQUIRIDO [S]I [N]O?" , "ERROR, LA OPCION DIGITA NO SE ENCUENTRA EN LAS OPCIONES DISPONIBLES \nINTENTE DE NUEVO")
            if mod_cliente.upper()=="S":
              _cantidad = regular_input("^([0-9])+$","MODIFICA LA CANTIDAD DE PRODUCTOS ADQUIRIDOS:","error")
              cantidad = int(_cantidad)
              facturas[_id_facturas][2][i][1] = cantidad

            mod_cliente=regular_input("^([S,s,N,n]{0,1})$","DESEA MODIFICAR EL PRODUCTO QUE ADQUIRIO [S]I [N]O?" , "ERROR, LA OPCION DIGITA NO SE ENCUENTRA EN LAS OPCIONES DISPONIBLES \nINTENTE DE NUEVO")
            if mod_cliente.upper()=="S":
              while True:
                _id_producto=regular_input("^([0-9])+$","A CONTINUACION DIGITARAS EL ID DEL PRODUCTO ADQUIRIDO \nTIENES UN LIMITE DE 256 CARACTERES ","ERROR, EXCEDIO EL LIMITE DE CARACTERES INTENTE DE NUEVO")
                id_producto = int(_id_producto)
                if not(id_producto in productos.keys()):
                  print("ese id no existe")
                  continue
                facturas[_id_facturas][2][i][0] = id_producto
                facturas[_id_facturas][2][i][2] = productos[id_producto][1]
                facturas[_id_facturas][2][i][3] = productos[id_producto][2]
                facturas[_id_facturas][2][i][4] = productos[id_producto][3]
                break
      
    else:
      create_opcion = regular_input("^([C,c,r,R])$","EL IDENTIFICADOR QUE USTED PROPORCIONO NO SE ENCUENTRA EN NUESTROS DESEA: [C]CREARLO  O [R]EGRESAR","EL PARTRON NO ES EL CORRECTO")
      if create_opcion.upper()=="C":
          while True: #CREACION DE EL ID DEL CLIENTE SE VALIDA QUE ESTE ESTE PREVIAMENTE REGISTRADO
            elementos = []
            _id_cliente=regular_input("^([0-9])+$","A CONTINUACION MODIFICACARAS DIGITARAS EL ID DEL COMPRADOR PREVIAMENTE REGISTRADO \nTIENES UN LIMITE DE 256 CARACTERES ","ERROR, EXCEDIO EL LIMITE DE CARACTERES INTENTE DE NUEVO")
            id_cliente = int(_id_cliente)
            if not(id_cliente in clientes.keys()):
              print("ESE IDENTIFICADOR NO SE ENCUENTRA DISPONIBLE")
              continue
            elementos.append(id_cliente)
            print("Su movimiento ha sido generado existosamente")
            break

          fecha = dt.datetime.now() #CREAR DE LA FECHA A LA FECHA ACTUAL
          fecha = dt.datetime.strftime(fecha,"%D")
          elementos.append(fecha)

          i = 0
          detalles = {}
          while True:#CREACION DE LAS PROPIDADES DE LAS FACTURAS SE INICIA UN CICLO FOR PARA RECORRER EL DICCIONARIO
            elementos_detalles = []
            i+=1
            while True:#CREACION DE EL ID PRODUCTO ESTA VALIDA QUE EXISTA EN NUESTRO DICIIONARIO PRODUCTOS
              _id_producto=regular_input("^([0-9])+$","A CONTINUACION DIGITARAS EL ID DEL PRODUCTO ADQUIRIDO\nTIENES UN LIMITE DE 256 CARACTERES ","ERROR, EXCEDIO EL LIMITE DE CARACTERES INTENTE DE NUEVO")
              id_producto = int(_id_producto)
              if not(id_producto in productos.keys()):
                print("EL IDENTIFICADOR DE ESE PRODUCTO NO ESTA DISPONIBLE")
                continue
              elementos_detalles.append(id_producto)  
              break

            _cantidad = regular_input("^([0-9])+$","CUANTA CANTIDAD DE PRODUCTO ADQUIRIO","error")
            cantidad = int(_cantidad)
            elementos_detalles.append(cantidad)
            elementos_detalles.append(productos[id_producto][1])
            elementos_detalles.append(productos[id_producto][2])
            elementos_detalles.append(productos[id_producto][3])
            detalles[i] = elementos_detalles

            mod_cliente=regular_input("^([S,s,N,n]{0,1})$","TIENES ALGUN DETALLE DE COMPRA POR AÑADIR [S]I [N]O?" , "ERROR, LA OPCION DIGITA NO SE ENCUENTRA EN LAS OPCIONES DISPONIBLES \nINTENTE DE NUEVO")
            if mod_cliente.upper()=="N":
              elementos.append(detalles)
              break     
          facturas[_id_facturas] = elementos
          print("su creacion se realizo con exito")

def txt_facturas(id_factura):
  global productos,facturas
  suma = 0
  print("--------------------------------------------------------------")
  print("                     * LIBRERIA CORP *                            ")
  print(f"CODIGO DE VENTA:{id_factura}                    FECHA DE ADQUISISION:{facturas[id_factura][0]}\n\n")
  for i in facturas[id_factura][2].keys():
    print(f"{facturas[id_factura][2][i][1]} {productos[facturas[id_factura][2][i][0]][0]}: {facturas[id_factura][2][i][2]*facturas[id_factura][2][i][1]}")
    print(f"IMPUESTO:{facturas[id_factura][2][i][2]*facturas[id_factura][2][i][4]}")
    suma += facturas[id_factura][2][i][2]*facturas[id_factura][2][i][1]
  
  print(f"\n                        SUB TOTAL (IMPUESTOS INCLUIDOS):{suma}")
  
while True:
  opcion_general=regular_input("^([F,P,C,f,c,p,t,T]{0,1})$", "BIENVENIDO ELIGA UNA OPCION \n[C]lientes [F]acturas [P]roductos  [T]erminar\n", "ERROR, ELIGA UNA OPCION DEL MENU, INTENTE DE NUEVO")
  if opcion_general.upper() == "T":
    break
  if opcion_general.upper()=="P":
    CRUD_P()#esta condicion nos lleva a la seccion de productos
  elif opcion_general.upper() == "C":
    CRUD_c()#esto es en caso de que el ususario eliga hacer la seccion en clientes
  elif opcion_general.upper() == "F":
    CRUD_FACTURAS()#esta condicion nos lleva a la seccion de facturas
    
json_string=json.dumps(db)
print(json_string)
