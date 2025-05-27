<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora de Precios de Vehículos</title>
    <style>
        /* ESTILOS GENERALES */
        * {
            margin: 0;
            padding: 0; 
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }
        
        body {
            background-color: #8fcff1;
            padding: 20px;
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
            background-color: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            border: 2px solid #5dc9ee;
        }
        
        h1 {
            text-align: center;
            color: #0de523;
            margin-bottom: 30px;
        }
        
        p {
            text-align: center;
            color: #02666b;
            margin-bottom: 30px;
        }
        
        /* ESTILOS DEL FORMULARIO */
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: #60e0f7;
        }
        
        /* Estilos para campos de texto, número y menú desplegable */
        input[type="text"],
        input[type="number"],
        select {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
            transition: border-color 0.3s ease;
        } 

        input[type="text"]:focus,
        input[type="number"]:focus,
        select:focus {
           border-color: #3498db;
           outline: none;
           box-shadow: 0 0 5px rgba(81, 175, 237, 0.3);
        
        /* Estilos específicos para el checkbox */
        input[type="checkbox"] {
            margin-right: 10px;
            transform: scale(1.2);
        }
        
        /* Estilos para el botón */
        button {
            background-color: #3498db;
            color: white;
            border: none;
            padding: 12px 20px;
            font-size: 16px;
            border-radius: 5px;
            cursor: pointer;
            display: block;
            width: 100%;
            margin-top: 20px;
        }
        
        /* Estilos cuando el cursor pasa sobre el botón */
        button:hover {
            background-color: #3e8e41;
            background-color: #2980b9;
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);

        }

        #reiniciarBtn:hover {
            background-color: #3498db !important;
       
        }
        
        /* ESTILOS DEL ÁREA DE RESULTADOS */
        .resultado {
            margin-top: 30px;
            padding: 20px;
            background-color: #f9f9f9;
            border-radius: 5px;
            border-left: 5px solid #4CAF50;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        .resultado h2 {
            color: #12d9bb;
            margin-bottom: 15px;
        }
        
        .resultado p {
            margin-bottom: 10px;
            font-size: 16px;
            color: #09c0b4;
        }
        
        /* Estilo especial para el precio final */
        #resultadoPrecioFinal {
            font-size: 20px;
            font-weight: bold;
            color: #4CAF50;
            margin-top: 15px;
            padding: 10px;
            background-color: #29afd0;
            border-radius: 8px;
            text-align: center;
        }
        
        /* ESTILOS PARA LA SECCIÓN EXPLICATIVA */
        .steps {
            margin-top: 50px; /* Espacio de 50px arriba de la sección */
            background-color: #f0f8ff; /* Fondo azul muy claro */
            padding: 20px; /* Relleno interior de 20px */
            border-radius: 5px; /* Esquinas redondeadas con radio de 5px */
        }
        
        .steps h2 {
            margin-bottom: 15px; /* Espacio de 15px debajo del título */
            color: #0066cc; /* Color azul para el título */
        }
        
        .steps ol {
            padding-left: 20px; /* Espacio de 20px a la izquierda (para los números) */
        }
        
        .steps li {
            margin-bottom: 10px; /* Espacio de 10px entre elementos de la lista */
            line-height: 1.5; /* Altura de línea para mejor legibilidad */
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Calculadora de Precios de Vehículos</h1>
        <p>Esta página nos permitirá calcular el precio final de un vehículo.</p>
        
        <!-- Formulario para recoger los datos del usuario -->
        <form id="vehiculoForm">
            <!-- Grupo para el nombre del cliente -->
            <div class="form-group">
                <label for="cliente">Nombre del Cliente:</label>
                <input type="text" id="cliente" placeholder="Ingrese el nombre del cliente" required>
            </div>
            
            <!-- Grupo para la selección de vehículo -->
            <div class="form-group">
                <label for="vehiculo">Seleccione el Vehículo:</label>
                <select id="vehiculo" required>
                    <option value="">-- Seleccione un vehículo --</option>
                    <option value="Toyota Corolla">Toyota Corolla</option>
                    <option value="Honda Civic">Honda Civic</option>
                    <option value="Ford Mustang">Ford Mustang</option>
                    <option value="Chevrolet Camaro">Chevrolet Camaro</option>
                    <option value="BMW Serie 3">BMW Serie 3</option>
                    <option value="Mercedes-Benz Clase C">Mercedes-Benz Clase C</option>
                    <option value="Audi A4">Audi A4</option>
                    <option value="Nissan Altima">Nissan Altima</option>
                    <option value="Hyundai Elantra">Hyundai Elantra</option>
                    <option value="Mazda 6">Mazda 6</option>
                    <option value="Volkswagen Jetta">Volkswagen Jetta</option>
                    <option value="Subaru Impreza">Subaru Impreza</option>
                </select>
            </div>
            
            <!-- Grupo para el precio del vehículo -->
            <div class="form-group">
                 <label for="precio">Precio del Vehículo:</label>
                 <input type="number" id="precio" placeholder="Ingrese el precio del vehículo" required>

            </div>

             <!-- Grupo para el checkbox de Seguro -->
            <div class="form-group">
                <label>
                    <input type="checkbox" id="aplicarSeguro"> 
                    Incluir Seguro (+$1,200)
                </label>
            </div>
            
            <!-- Grupo para el checkbox de IVA -->
            <div class="form-group">
                <label>
                    <input type="checkbox" id="aplicarIVA"> 
                    Aplicar IVA (15%)
                </label>
            </div>
        
             <!-- Botón para realizar el cálculo -->
             <div style="display: flex; gap: 300px;">
             <!-- Botón de calcular precio final -->
                 <button type="button" id="calcularBtn">Calcular Precio Final</button>

              <!-- Botón de reiniciar formulario -->
                 <button type="button" id="reiniciarBtn" style="flex: 1; background-color: #63f3ad;">Reiniciar Formulario</button>
             </div>
        </form>
        
        <!-- Sección donde se mostrarán los resultados (inicialmente oculta) -->
        <div id="resultado" class="resultado" style="display: none;">
            <h2>Resultado del Cálculo</h2>
            <p id="resultadoCliente"></p>
            <p id="resultadoVehiculo"></p>
            <p id="resultadoPrecioBase"></p>
            <p id="resultadoDescuento"></p>
            <p id="resultadoIVA"></p>
            <p id="resultadoPrecioFinal"></p>
            <p id="resultadoSeguro"></p>
        </div>
        
        <!-- Sección explicativa para estudiantes -->
        <div class="steps">
            <h2>Guía para Estudiantes: Cómo Funciona Esta Página</h2>
            <ol>
                <li>Creamos un formulario HTML con campos para ingresar datos.</li>
                <li>Aplicamos estilos CSS para mejorar la apariencia.</li>
                <li>Usamos JavaScript para capturar los datos y realizar cálculos.</li>
                <li>Si el precio es mayor a $50,000, aplicamos un descuento del 15%.</li>
                <li>Si se marca la casilla de IVA, sumamos un 15% al precio.</li>
                <li>Finalmente, mostramos el resultado en la sección superior.</li>
            </ol>
        </div>
    </div>

    <script>
        // Este evento se dispara cuando el documento HTML está completamente cargado
        document.addEventListener('DOMContentLoaded', function() {
            // Obtenemos referencias a los elementos del formulario utilizando sus identificadores
            const clienteInput = document.getElementById('cliente');         // Campo de texto del cliente
            const vehiculoSelect = document.getElementById('vehiculo');      // Menú desplegable de vehículos
            const precioInput = document.getElementById('precio');           // Campo numérico del precio
            const aplicarIVACheckbox = document.getElementById('aplicarIVA'); // Checkbox del IVA
            const calcularBtn = document.getElementById('calcularBtn');       // Botón de calcular
            const resultadoDiv = document.getElementById('resultado');        // Div que mostrará los resultados
            const aplicarSeguroCheckbox = document.getElementById('aplicarSeguro');
            const reiniciarBtn = document.getElementById('reiniciarBtn');
            
            // Configuramos un "escuchador de eventos" para el clic en el botón
            calcularBtn.addEventListener('click', calcularPrecioFinal);
            reiniciarBtn.addEventListener('click', reiniciarFormulario);
            
            // Definimos la función que realizará todos los cálculos
            function calcularPrecioFinal() {
                // 1. CAPTURAR LOS VALORES INGRESADOS POR EL USUARIO
                
                // Obtenemos el texto del campo nombre y eliminamos espacios al inicio/final
                const cliente = clienteInput.value.trim();
                
                // Obtenemos el valor seleccionado en el menú desplegable
                const vehiculo = vehiculoSelect.value;
                
                // Convertimos el texto del campo precio a un número decimal
                const precioBase = parseFloat(precioInput.value);
                
                // Verificamos si el checkbox de IVA está marcado
                const aplicarIVA = aplicarIVACheckbox.checked;
                const aplicarSeguro = aplicarSeguroCheckbox.checked;
                
                // 2. VALIDAR QUE TODOS LOS CAMPOS REQUERIDOS ESTÉN COMPLETOS
                
                // Verificamos que el nombre no esté vacío, que se haya seleccionado un vehículo,
                // que el precio sea un número válido y que sea mayor que cero
                if (cliente === '' || vehiculo === '' || isNaN(precioBase) || precioBase <= 0) {
                    alert('Por favor, complete todos los campos correctamente.');
                    return; // Detiene la ejecución de la función
                }

                if (vehiculo === '' || isNaN(precioBase) || precioBase <= 0) {
                    alert('Por favor, complete todos los campos correctamente.');
                return;
                }
                
                // 3. CALCULAR EL DESCUENTO (10% si el precio es mayor a 40000)
                
                let descuento = 0;
                
                if (precioBase > 50000) {
                    // Calculamos el 10% del precio base
                    descuento = precioBase * 0.15;
                }
                
                // 4. CALCULAR EL PRECIO CON DESCUENTO
                
                const precioDespuesDescuento = precioBase - descuento;
                
                // 5. CALCULAR EL IVA (15% si está seleccionado)
                
                let iva = 0;
                
                if (aplicarIVA) {
                    // Calculamos el 15% del precio con descuento
                    iva = precioDespuesDescuento * 0.15;
                }

                // 6. CALCULAR EL COSTO DEL SEGURO ($1,200 si está seleccionado)
                let seguro = 0;

                if (aplicarSeguro) {
                   seguro = 1200;
                }
                
                // 7. CALCULAR EL PRECIO FINAL
                
                const precioFinal = precioDespuesDescuento + iva + seguro;
                
                // 8. MOSTRAR LOS RESULTADOS EN EL DIV
                
                document.getElementById('resultadoCliente').textContent = 'Cliente: ' + cliente;
                document.getElementById('resultadoVehiculo').textContent = 'Vehículo: ' + vehiculo;
                document.getElementById('resultadoPrecioBase').textContent = 'Precio Base: $' + precioBase.toFixed(2);
                
                // Solo mostrar mensaje de descuento si se aplicó algún descuento
                if (descuento > 0) {
                    document.getElementById('resultadoDescuento').textContent = 'Descuento (10%): -$' + descuento.toFixed(2);
                } else {
                    document.getElementById('resultadoDescuento').textContent = 'Descuento: No aplicado';
                }
                
                // Solo mostrar mensaje de IVA si se seleccionó aplicarlo
                if (aplicarIVA) {
                    document.getElementById('resultadoIVA').textContent = 'IVA (15%): +$' + iva.toFixed(2);
                } else {
                    document.getElementById('resultadoIVA').textContent = 'IVA: No aplicado';
                }
                
                // Mostramos el precio final con formato
                document.getElementById('resultadoPrecioFinal').textContent = 'PRECIO FINAL: $' + precioFinal.toFixed(2);
                
                if (aplicarSeguro) {
                    document.getElementById('resultadoSeguro').textContent = 'Seguro: +$' + seguro.toFixed(2);
                } else {
                document.getElementById('resultadoSeguro').textContent = 'Seguro: No aplicado';
                }

                // 8. MOSTRAR EL DIV DE RESULTADOS
                
                resultadoDiv.style.display = 'block';
                
                // 9. HACER SCROLL AL RESULTADO
                
                resultadoDiv.scrollIntoView({ behavior: 'smooth' });

                function reiniciarFormulario() {
                   clienteInput.value = '';
                   vehiculoSelect.value = '';
                   precioInput.value = '';
                   aplicarIVACheckbox.checked = false;
                   aplicarSeguroCheckbox.checked = false;
                   resultadoDiv.style.display = 'none';
                   document.querySelector('h1').scrollIntoView({ behavior: 'smooth' });
                }
            }
        });
    </script>
</body>
</html>
