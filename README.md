<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dulces Sueños Tejidos - Tienda Artesanal</title>
    <style>
        * {
            box-sizing: border-box;
        }
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #FFF8F0;
            color: #333;
        }
        header {
            background-color: #F4C2C2;
            color: white;
            padding: 20px;
            text-align: center;
            position: relative;
        }
        nav {
            display: flex;
            justify-content: center;
            background-color: #87CEEB;
            padding: 10px;
            position: sticky;
            top: 0;
            z-index: 90;
        }
        nav a {
            color: white;
            margin: 0 15px;
            text-decoration: none;
            font-weight: bold;
        }
        nav a:hover {
            text-decoration: underline;
        }
        section {
            padding: 20px;
            max-width: 1200px;
            margin: 0 auto;
        }

        /* Filtros y Búsqueda */
        .filtros-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
            gap: 15px;
            margin-bottom: 25px;
            background: white;
            padding: 15px 20px;
            border-radius: 10px;
            box-shadow: 0 2px 6px rgba(0,0,0,0.06);
        }
        .busqueda-input {
            padding: 10px 14px;
            border: 1px solid #ddd;
            border-radius: 20px;
            width: 260px;
            font-size: 14px;
            outline: none;
        }
        .busqueda-input:focus {
            border-color: #87CEEB;
        }
        .categoria-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }
        .tag-btn {
            background-color: #f0f0f0;
            border: 1px solid #ddd;
            padding: 7px 15px;
            border-radius: 18px;
            cursor: pointer;
            font-weight: bold;
            font-size: 13px;
            color: #555;
            transition: all 0.2s;
        }
        .tag-btn.active, .tag-btn:hover {
            background-color: #6B5B95;
            color: white;
            border-color: #6B5B95;
        }
        .btn-guia-tallas {
            background-color: #87CEEB;
            color: white;
            border: none;
            padding: 7px 15px;
            border-radius: 18px;
            cursor: pointer;
            font-weight: bold;
            font-size: 13px;
            transition: background 0.2s;
        }
        .btn-guia-tallas:hover {
            background-color: #5bb3d6;
        }

        /* Cuadrícula de Productos */
        .productos {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-around;
        }
        .producto {
            background-color: white;
            border: 1px solid #ddd;
            border-radius: 10px;
            margin: 10px;
            padding: 15px;
            width: 30%;
            text-align: center;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            position: relative;
        }
        .producto:hover {
            transform: translateY(-5px);
        }
        .producto.agotado {
            opacity: 0.75;
            filter: grayscale(0.2);
        }
        .badge-agotado {
            position: absolute;
            top: 15px;
            left: 15px;
            background: #d9534f;
            color: white;
            padding: 4px 10px;
            border-radius: 12px;
            font-size: 12px;
            font-weight: bold;
            z-index: 5;
        }
        .producto img {
            max-width: 100%;
            border-radius: 10px;
            cursor: pointer;
            height: 200px;
            object-fit: cover;
        }
        .producto h3 {
            color: #6B5B95;
            margin: 10px 0;
        }
        .producto p {
            font-size: 14px;
            color: #555;
            margin: 5px 0;
            flex-grow: 1;
        }
        .producto .precio {
            font-weight: bold;
            color: #FF6F61;
            font-size: 18px;
            margin: 10px 0;
        }
        .variantes-producto {
            display: flex;
            gap: 8px;
            margin: 10px 0;
        }
        .variantes-producto select {
            flex: 1;
            padding: 8px 6px;
            border: 1px solid #ddd;
            border-radius: 6px;
            font-size: 12px;
            background: #fff;
            color: #333;
        }
        .producto button.btn-add {
            background-color: #FF6F61;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            margin: 5px 0 0 0;
            transition: background-color 0.3s;
            font-weight: bold;
            width: 100%;
        }
        .producto button.btn-add:hover {
            background-color: #FF3B2F;
        }
        .producto button.btn-add:disabled {
            background-color: #bbb;
            cursor: not-allowed;
        }

        /* Estilos del carrito */
        .carrito-icono {
            position: absolute;
            top: 20px;
            right: 20px;
            cursor: pointer;
            font-size: 24px;
            color: white;
            display: flex;
            align-items: center;
            user-select: none;
        }
        .carrito-contador {
            background: #FF6F61;
            border-radius: 50%;
            width: 24px;
            height: 24px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 14px;
            margin-left: 5px;
        }
        .carrito-contenido {
            display: none;
            position: fixed;
            top: 80px;
            right: 20px;
            background-color: white;
            width: 390px;
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.25);
            z-index: 100;
            max-height: 80vh;
            overflow-y: auto;
        }
        .carrito-item {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 12px;
            border-bottom: 1px solid #eee;
            padding-bottom: 10px;
        }
        .carrito-item-img {
            width: 52px;
            height: 52px;
            border-radius: 6px;
            object-fit: cover;
            border: 1px solid #eee;
        }
        .carrito-item-info {
            flex-grow: 1;
            font-size: 13px;
            text-align: left;
        }
        .carrito-item-nombre {
            font-weight: bold;
            color: #333;
            display: block;
        }
        .carrito-item-detalle {
            color: #777;
            font-size: 11px;
            margin-top: 2px;
        }
        .carrito-item-precio {
            color: #FF6F61;
            font-weight: bold;
            font-size: 12px;
        }
        .carrito-item-cantidad {
            display: flex;
            align-items: center;
        }
        .carrito-item-cantidad button {
            background: #87CEEB;
            border: none;
            width: 22px;
            height: 22px;
            border-radius: 50%;
            cursor: pointer;
            color: white;
            font-weight: bold;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .carrito-item-cantidad button:hover {
            background: #6B5B95;
        }
        .carrito-item-cantidad span {
            margin: 0 6px;
            min-width: 16px;
            text-align: center;
            font-weight: bold;
        }
        .carrito-item-subtotal {
            min-width: 70px;
            text-align: right;
            font-weight: bold;
            font-size: 13px;
        }
        .carrito-total {
            font-weight: bold;
            text-align: right;
            margin-top: 15px;
            font-size: 1.2em;
            padding-top: 10px;
            border-top: 2px solid #6B5B95;
            color: #6B5B95;
        }
        .carrito-acciones {
            display: flex;
            justify-content: space-between;
            margin-top: 15px;
            gap: 10px;
        }
        .carrito-acciones button {
            flex: 1;
            padding: 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
        }
        #vaciar-carrito {
            background: #f8d7da;
            color: #721c24;
        }
        #vaciar-carrito:hover {
            background: #f5c6cb;
        }
        #comprar-carrito {
            background: #d4edda;
            color: #155724;
        }
        #comprar-carrito:hover {
            background: #c3e6cb;
        }

        /* Modales */
        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            overflow-y: auto;
        }
        .modal-content {
            background-color: #FFF8F0;
            margin: 30px auto;
            padding: 25px;
            border-radius: 10px;
            width: 90%;
            max-width: 550px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
            position: relative;
        }
        .close {
            position: absolute;
            top: 15px;
            right: 20px;
            color: #6B5B95;
            font-size: 28px;
            font-weight: bold;
            cursor: pointer;
        }
        .close:hover {
            color: #FF6F61;
        }
        .form-group {
            margin-bottom: 12px;
        }
        .form-group label {
            display: block;
            margin-bottom: 4px;
            color: #6B5B95;
            font-weight: bold;
            font-size: 13px;
        }
        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 9px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-family: inherit;
            font-size: 14px;
        }

        /* Nequi */
        .opciones-pago {
            display: flex;
            gap: 15px;
            margin-bottom: 12px;
        }
        .opciones-pago label {
            display: flex;
            align-items: center;
            gap: 6px;
            cursor: pointer;
            font-weight: normal;
        }
        .caja-nequi {
            background: #fdf1f7;
            border: 2px dashed #e02b78;
            border-radius: 8px;
            padding: 15px;
            text-align: center;
            margin-bottom: 15px;
        }
        .caja-nequi h4 {
            color: #e02b78;
            margin: 0 0 6px 0;
        }
        .nequi-fila-numero {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            margin: 8px 0;
        }
        .nequi-numero {
            font-size: 22px;
            font-weight: bold;
            color: #333;
            letter-spacing: 1px;
        }
        .btn-copiar {
            background-color: #e02b78;
            color: white;
            border: none;
            padding: 5px 10px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 12px;
            font-weight: bold;
        }
        .btn-copiar:hover {
            opacity: 0.85;
        }
        .caja-nequi img {
            width: 140px;
            height: 140px;
            margin: 10px auto;
            border: 1px solid #ddd;
            border-radius: 8px;
            background: white;
            padding: 5px;
            display: block;
        }

        .tabla-medidas {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
            background: white;
            border-radius: 8px;
            overflow: hidden;
        }
        .tabla-medidas th, .tabla-medidas td {
            border: 1px solid #eee;
            padding: 10px;
            text-align: center;
            font-size: 13px;
        }
        .tabla-medidas th {
            background-color: #87CEEB;
            color: white;
        }

        .btn-submit {
            background-color: #FF6F61;
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
            font-size: 16px;
            font-weight: bold;
            transition: background-color 0.3s;
            margin-top: 8px;
        }
        .btn-submit:hover {
            background-color: #FF3B2F;
        }

        .notificacion {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: #4CAF50;
            color: white;
            padding: 12px 20px;
            border-radius: 5px;
            z-index: 2000;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
            transition: opacity 0.4s ease;
            font-size: 14px;
        }

        /* Panel Administrativo Oculto */
        #admin-panel {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.7);
            z-index: 5000;
            overflow-y: auto;
        }
        .admin-box {
            background: white;
            width: 95%;
            max-width: 850px;
            margin: 30px auto;
            padding: 25px;
            border-radius: 12px;
        }
        .admin-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid #eee;
            padding-bottom: 10px;
            margin-bottom: 20px;
        }
        .admin-item {
            background: #fafafa;
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 15px;
        }
        .admin-item-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
            margin-bottom: 10px;
        }
        .admin-item-grid full {
            grid-column: 1 / -1;
        }
        .btn-admin-save {
            background: #28a745;
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 6px;
            font-weight: bold;
            cursor: pointer;
            font-size: 15px;
        }
        .btn-admin-nuevo {
            background: #6B5B95;
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 6px;
            font-weight: bold;
            cursor: pointer;
            margin-bottom: 15px;
        }
        .btn-admin-delete {
            background: #dc3545;
            color: white;
            border: none;
            padding: 6px 12px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 12px;
        }
        /* Botón Invisible de Acceso */
        #secret-admin-trigger {
            opacity: 0.01;
            cursor: default;
            user-select: none;
            display: inline-block;
        }

        @media (max-width: 900px) {
            .producto {
                width: 45%;
            }
            .admin-item-grid {
                grid-template-columns: 1fr;
            }
        }
        @media (max-width: 600px) {
            .producto {
                width: 100%;
            }
            .carrito-contenido {
                width: 92%;
                right: 4%;
                left: 4%;
            }
            .filtros-container {
                flex-direction: column;
                align-items: stretch;
            }
            .busqueda-input {
                width: 100%;
            }
        }
        footer {
            background-color: #6B5B95;
            color: white;
            text-align: center;
            padding: 20px;
            margin-top: 30px;
        }
        .whatsapp {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: #25D366;
            color: white;
            padding: 15px;
            border-radius: 50%;
            text-decoration: none;
            font-size: 24px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
            z-index: 99;
        }
    </style>
</head>
<body>
    <header>
        <h1>Dulces Sueños Tejidos</h1>
        <p>Magia y calidez para tu bebé</p>
        <div class="carrito-icono" id="carrito-icono">
            🛒 <span class="carrito-contador" id="carrito-contador">0</span>
        </div>
        <div class="carrito-contenido" id="carrito-contenido">
            <h3>Tu Carrito</h3>
            <div id="carrito-items"></div>
            <div class="carrito-total">Total: $<span id="carrito-total">0</span></div>
            <div class="carrito-acciones">
                <button type="button" id="vaciar-carrito">Vaciar Carrito</button>
                <button type="button" id="comprar-carrito">Comprar</button>
            </div>
        </div>
    </header>

    <nav>
        <a href="#inicio">Inicio</a>
        <a href="#catalogo">Catálogo</a>
        <a href="#contacto">Contacto</a>
        <a href="#nosotros">Sobre Nosotros</a>
    </nav>

    <section id="inicio">
        <h2>Bienvenidos a Dulces Sueños Tejidos</h2>
        <p>En nuestra tienda de tejidos artesanales, nos dedicamos a crear piezas únicas y de alta calidad para tu bebé. Descubre la ternura y calidez de nuestros productos, cada uno confeccionado con amor y materiales suaves para brindar comodidad y estilo.</p>
        <p>Desde gorritos y zapatitos hasta conjuntos completos, cada pieza está diseñada pensando en el bienestar de tu pequeño.</p>
    </section>

    <section id="catalogo">
        <h2>Nuestros Productos</h2>
        
        <div class="filtros-container">
            <div class="categoria-tags">
                <button type="button" class="tag-btn active" onclick="filtrarCategoria('todos')">Todos</button>
                <button type="button" class="tag-btn" onclick="filtrarCategoria('conjuntos')">Conjuntos</button>
                <button type="button" class="tag-btn" onclick="filtrarCategoria('gorros')">Gorros</button>
                <button type="button" class="tag-btn" onclick="filtrarCategoria('calzado')">Calzado</button>
                <button type="button" class="tag-btn" onclick="filtrarCategoria('accesorios')">Accesorios</button>
            </div>
            <input type="text" id="busqueda-producto" class="busqueda-input" placeholder="Buscar producto..." oninput="buscarProductos()">
            <button type="button" class="btn-guia-tallas" onclick="abrirGuiaTallas()">📏 Guía de Medidas</button>
        </div>

        <div class="productos" id="productos-container"></div>
    </section>

    <section id="contacto">
        <h2>Contacto</h2>
        <div>
            <p>¿Tienes preguntas o quieres un pedido especial? ¡Contáctanos!</p>
            <p>Teléfono: <a href="tel:3222156178">322 215 6178</a></p>
            <p>Horario: Lunes a Viernes 9:00 am - 6:00 pm</p>
            <p>Ubicación: Soatá, Boyacá</p>
        </div>
    </section>

    <section id="nosotros">
        <h2>Sobre Nosotros</h2>
        <p>Somos un emprendimiento familiar ubicado en Soatá, Boyacá, especializado en la creación de tejidos artesanales para bebés. Con años de experiencia en el arte del tejido, nos enorgullece ofrecer productos de alta calidad y un servicio personalizado.</p>
        <p>Realizamos envíos a todo el país, tanto al por mayor como al detal, llevando calidez y ternura a cada hogar colombiano.</p>
    </section>

    <!-- Modal de Compra Rápida -->
    <div id="modalCompra" class="modal">
        <div class="modal-content">
            <span class="close" id="close-modal">&times;</span>
            <h2>Finalizar Pedido</h2>
            <form id="formulario-compra">
                <div class="form-group">
                    <label for="nombre-completo">Nombre y Apellido *</label>
                    <input type="text" id="nombre-completo" required placeholder="Tu nombre completo">
                </div>
                
                <div class="form-group">
                    <label for="celular">Celular *</label>
                    <input type="tel" id="celular" required placeholder="Ej: 3201234567">
                </div>

                <div class="form-group">
                    <label for="email">Correo Electrónico (Opcional)</label>
                    <input type="email" id="email" placeholder="correo@ejemplo.com">
                </div>

                <div class="form-group">
                    <label for="departamento">Departamento *</label>
                    <select id="departamento" required>
                        <option value="">Seleccione un departamento...</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="ciudad-input">Ciudad / Municipio (Escribe o busca) *</label>
                    <input list="lista-ciudades" id="ciudad-input" required placeholder="Seleccione un departamento primero..." disabled>
                    <datalist id="lista-ciudades"></datalist>
                </div>
                
                <div class="form-group">
                    <label for="direccion">Dirección completa y barrio *</label>
                    <textarea id="direccion" rows="2" required placeholder="Ej: Carrera 4 # 10-25, Barrio Centro"></textarea>
                </div>

                <div class="form-group">
                    <label>Forma de Pago:</label>
                    <div class="opciones-pago">
                        <label>
                            <input type="radio" name="metodo-pago" value="nequi" checked id="radio-nequi">
                            Nequi
                        </label>
                        <label>
                            <input type="radio" name="metodo-pago" value="acordar" id="radio-acordar">
                            Acordar por WhatsApp
                        </label>
                    </div>
                </div>

                <div id="info-nequi" class="caja-nequi">
                    <h4>Paga fácil con Nequi</h4>
                    <p>Envía o transfiere el valor total a la cuenta:</p>
                    <div class="nequi-fila-numero">
                        <span class="nequi-numero" id="numero-nequi-texto">3222156178</span>
                        <button type="button" class="btn-copiar" onclick="copiarNequi()">Copiar</button>
                    </div>
                    <img id="qr-nequi" src="" alt="Código QR Nequi">
                    <p><small>Escanea desde tu app o copia el número</small></p>
                    <div class="form-group" style="text-align: left; margin-top: 10px;">
                        <label for="comprobante-nequi" style="color: #e02b78; font-size: 12px;">Número de referencia o comprobante (opcional):</label>
                        <input type="text" id="comprobante-nequi" placeholder="Ej: M12345678">
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="notas">Notas adicionales:</label>
                    <textarea id="notas" rows="2" placeholder="Indicaciones de entrega, referencias, etc."></textarea>
                </div>
                
                <button type="submit" class="btn-submit">Enviar Pedido por WhatsApp</button>
            </form>
        </div>
    </div>

    <!-- Modal Guía de Tallas -->
    <div id="modalTallas" class="modal">
        <div class="modal-content">
            <span class="close" onclick="cerrarGuiaTallas()">&times;</span>
            <h2>Guía de Medidas (Bebé)</h2>
            <p style="font-size: 13px; color: #555;">Medidas estándar recomendadas por meses de edad:</p>
            <table class="tabla-medidas">
                <thead>
                    <tr>
                        <th>Talla / Edad</th>
                        <th>Cabeza (Gorros)</th>
                        <th>Pie (Zapatos)</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><strong>Recién Nacido</strong></td>
                        <td>33 - 36 cm</td>
                        <td>8 - 9 cm</td>
                    </tr>
                    <tr>
                        <td><strong>0 - 3 Meses</strong></td>
                        <td>36 - 40 cm</td>
                        <td>9 - 10 cm</td>
                    </tr>
                    <tr>
                        <td><strong>3 - 6 Meses</strong></td>
                        <td>40 - 43 cm</td>
                        <td>10 - 11 cm</td>
                    </tr>
                    <tr>
                        <td><strong>6 - 12 Meses</strong></td>
                        <td>43 - 46 cm</td>
                        <td>11 - 12 cm</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>

    <!-- Panel de Administración Oculto -->
    <div id="admin-panel">
        <div class="admin-box">
            <div class="admin-header">
                <h2>Panel Administrador de Productos</h2>
                <span class="close" onclick="cerrarAdmin()">&times;</span>
            </div>
            <button type="button" class="btn-admin-nuevo" onclick="agregarProductoVacio()">+ Añadir Nuevo Producto</button>
            <div id="admin-lista-productos"></div>
            <button type="button" class="btn-admin-save" onclick="guardarCambiosAdmin()">Guardar Todos los Cambios</button>
        </div>
    </div>

    <a href="https://wa.me/573222156178" class="whatsapp" target="_blank" title="Contactar por WhatsApp">
        <img src="https://upload.wikimedia.org/wikipedia/commons/6/6b/WhatsApp.svg" alt="WhatsApp" width="30">
    </a>

    <footer>
        <p>© 2026 Dulces Sueños Tejidos - Todos los derechos reservados <span id="secret-admin-trigger" onclick="abrirAdmin()">•</span></p>
    </footer>

    <script>
        const numeroNequi = "3222156178";

        // Base de datos de productos por defecto
        const productosPorDefecto = [
            { 
                id: 1, 
                categoria: "conjuntos",
                img: "https://i.imgur.com/fSCPxyu.jpg", 
                nombre: "Saco y manopla para bebé", 
                precio: 35000, 
                stock: true,
                descripcion: "Conjunto práctico diseñado para mantener a tu pequeño abrigado. Lana hipoalergénica.",
                tallas: ["0-3 meses", "3-6 meses", "6-12 meses"],
                colores: ["Blanco", "Palo de Rosa", "Azul Pastel", "Beige"]
            },
            { 
                id: 2, 
                categoria: "conjuntos",
                img: "https://i.imgur.com/aFgxCzQ.jpg", 
                nombre: "Conjunto completo 4 x 1", 
                precio: 60000, 
                stock: true,
                descripcion: "Incluye gorro, saco, patines y manoplas en suave tejido artesanal.",
                tallas: ["Recién Nacido", "0-3 meses", "3-6 meses"],
                colores: ["Blanco Puro", "Rosa Bebé", "Celeste", "Gris Perla"]
            },
            { 
                id: 3, 
                categoria: "conjuntos",
                img: "https://i.imgur.com/uRAX5jA.jpg", 
                nombre: "Esquimal para bebé", 
                precio: 40000, 
                stock: true,
                descripcion: "Conjunto abrigado ideal para días fríos y sesiones de fotos memorables.",
                tallas: ["0-3 meses", "3-6 meses", "6-12 meses"],
                colores: ["Gris con Blanco", "Café Claro", "Rosa Pastel", "Azul Marino"]
            },
            { 
                id: 4, 
                categoria: "calzado",
                img: "https://i.imgur.com/tiJobRZ.jpg", 
                nombre: "Zapatitos tejidos", 
                precio: 15000, 
                stock: true,
                descripcion: "Zapatitos con elástico suave que se ajusta a sus piecitos sin apretar.",
                tallas: ["0-3 meses (9cm)", "3-6 meses (10cm)", "6-12 meses (11cm)"],
                colores: ["Blanco", "Rojo", "Azul", "Rosa", "Amarillo"]
            },
            { 
                id: 5, 
                categoria: "accesorios",
                img: "https://i.imgur.com/CVD60u3.jpg", 
                nombre: "Moños para el cabello", 
                precio: 10000, 
                stock: true,
                descripcion: "Suaves moños con banda elástica que no maltrata la cabecita del bebé.",
                tallas: ["Talla Única"],
                colores: ["Surtido Niña", "Rojo", "Rosa", "Blanco"]
            },
            { 
                id: 6, 
                categoria: "accesorios",
                img: "https://i.imgur.com/dFqY8Fs.jpg", 
                nombre: "Apliques (Paquete x 6)", 
                precio: 10000, 
                stock: true,
                descripcion: "Pack de apliques en lana ideales para personalizar mantas o ropa.",
                tallas: ["Talla Única"],
                colores: ["Multicolor", "Tonos Pastel"]
            },
            { 
                id: 7, 
                categoria: "gorros",
                img: "https://i.imgur.com/CcRs4h4.jpg", 
                nombre: "Gorros para bebés", 
                precio: 25000, 
                stock: true,
                descripcion: "Protección térmica cómoda con orejitas o pompón suave.",
                tallas: ["0-3 meses", "3-6 meses", "6-12 meses"],
                colores: ["Blanco", "Beige", "Gris", "Rosa", "Azul"]
            },
            { 
                id: 8, 
                categoria: "gorros",
                img: "https://i.imgur.com/eDyzLbd.jpg", 
                nombre: "Gorros doble faz", 
                precio: 25000, 
                stock: false,
                descripcion: "Diseño reversible con dos opciones de color en una sola pieza.",
                tallas: ["0-3 meses", "3-6 meses"],
                colores: ["Gris / Rosa", "Azul / Blanco", "Beige / Café"]
            }
        ];

        // Directorio exhaustivo local de Colombia (32 departamentos + capital y sus municipios clave)
        const colombiaCompleta = {
            "AMAZONAS": ["Leticia", "Puerto Nariño", "El Encanto", "La Chorrera", "La Pedrera", "Mirití-Paraná", "Puerto Alegría", "Puerto Arica", "Puerto Santander", "Tarapacá"],
            "ANTIOQUIA": ["Medellín", "Bello", "Itagüí", "Envigado", "Apartadó", "Rionegro", "Turbo", "Caucasia", "Sabaneta", "Chigorodó", "Caldas", "Copacabana", "La Estrella", "Marinilla", "Guarne", "Santa Rosa de Osos", "Yarumal", "Sonsón", "Amagá", "Andes", "El Carmen de Viboral", "Frontino", "Urrao", "Segovia", "Remedios", "Santa Fe de Antioquia", "Necoclí", "San Pedro de los Milagros", "Jardín", "Jericó", "Guatapé"],
            "ARAUCA": ["Arauca", "Arauquita", "Cravo Norte", "Fortul", "Puerto Rondón", "Saravena", "Tame"],
            "ATLÁNTICO": ["Barranquilla", "Soledad", "Malambo", "Sabanalarga", "Baranoa", "Galapa", "Puerto Colombia", "Palmar de Varela", "Santo Tomás", "Campo de la Cruz", "Polonuevo", "Luruaco", "Repelón", "Juan de Acosta", "Tubará", "Usiacurí"],
            "BOGOTÁ, D.C.": ["Bogotá"],
            "BOLÍVAR": ["Cartagena", "Magangué", "El Carmen de Bolívar", "Turbaco", "Arjona", "San Juan Nepomuceno", "San Jacinto", "María la Baja", "Mompós", "Santa Rosa del Sur", "Achí", "Morales", "Simití", "Calamar", "Zambrano"],
            "BOYACÁ": ["Soatá", "Tunja", "Duitama", "Sogamoso", "Chiquinquirá", "Paipa", "Moniquirá", "Samacá", "Garagoa", "Guateque", "Nobsa", "Tibasosa", "Villa de Leyva", "Santa Rosa de Viterbo", "Boavita", "Susacón", "Tipacoque", "Covarachía", "La Uvita", "El Cocuy", "El Espino", "Güeicán", "Socha", "Paz de Río", "Tasco", "Miraflores", "Muzo", "Ramiriquí", "Ventaquemada"],
            "CALDAS": ["Manizales", "La Dorada", "Chinchiná", "Villamaría", "Anserma", "Riosucio", "Salamina", "Aguadas", "Neira", "Pensilvania", "Supía", "Manzanares", "Viterbo"],
            "CAQUETÁ": ["Florencia", "San Vicente del Caguán", "Cartagena del Chairá", "Puerto Rico", "El Doncello", "Paujil", "La Montañita", "Belén de los Andaquíes", "Solano", "Valparaíso"],
            "CASANARE": ["Yopal", "Aguazul", "Villanueva", "Tauramena", "Paz de Ariporo", "Maní", "Monterrey", "Trinidad", "Hato Corozal", "Orocué", "Nunchía"],
            "CAUCA": ["Popayán", "Santander de Quilichao", "Patía (El Bordo)", "Puerto Tejada", "Piendamó", "Bolívar", "El Tambo", "Silvia", "Guapi", "Timbío", "Miranda", "Caloto", "Corinto", "Inzá"],
            "CESAR": ["Valledupar", "Aguachica", "Codazzi", "Bosconia", "Curumaní", "El Paso", "Pailitas", "La Paz", "Chimichagua", "Chiriguaná", "San Alberto", "San Diego", "Pelaya"],
            "CHOCÓ": ["Quibdó", "Istmina", "Tadó", "Condoto", "El Carmen de Atrato", "Bahía Solano", "Nuquí", "Acandí", "Unguía", "Riosucio", "Bojayá"],
            "CÓRDOBA": ["Montería", "Lorica", "Cereté", "Sahagún", "Montelíbano", "Planeta Rica", "Tierralta", "Ciénaga de Oro", "Chinú", "Ayapel", "San Pelayo", "San Antero", "Pueblo Nuevo"],
            "CUNDINAMARCA": ["Soacha", "Facatativá", "Girardot", "Zipaquirá", "Chía", "Fusagasugá", "Mosquera", "Madrid", "Funza", "Cajicá", "Sopó", "Tocancipá", "Tabio", "Tenjo", "Cota", "Ubaté", "Villeta", "La Calera", "Gachancipá", "Pacho", "Silvania", "Guaduas", "Chocontá", "La Vega", "Subachoque"],
            "GUAINÍA": ["Inírida", "Barranco Minas", "Mapiripana", "San Felipe", "Puerto Colombia", "La Guadalupe", "Pana Pana", "Morichal"],
            "GUAVIARE": ["San José del Guaviare", "Calamar", "El Retorno", "Miraflores"],
            "HUILA": ["Neiva", "Pitalito", "Garzón", "La Plata", "Campoalegre", "San Agustín", "Gigante", "Palermo", "Aipe", "Rivera", "Timaná", "Algeciras", "Tarqui"],
            "LA GUAJIRA": ["Riohacha", "Maicao", "Uribia", "Manaure", "San Juan del Cesar", "Fonseca", "Barrancas", "Hatonuevo", "Villanueva", "Dibulla", "Albania"],
            "MAGDALENA": ["Santa Marta", "Ciénaga", "Fundación", "Plato", "El Banco", "Aracataca", "Pivijay", "Zona Bananera", "Santa Ana", "Sitio Nuevo", "Puebloviejo", "Guamal"],
            "META": ["Villavicencio", "Acacías", "Granada", "Puerto López", "San Martín", "Cumaral", "Puerto Gaitán", "Restrepo", "Guamal", "Vista Hermosa", "La Macarena", "Mesetas"],
            "NARIÑO": ["Pasto", "Ipiales", "Tumaco", "Túquerres", "La Unión", "Sandoná", "Samaniego", "Cumbal", "Ricaurte", "Barbacoas", "La Cruz", "Buesaco", "Taminango"],
            "NORTE DE SANTANDER": ["Cúcuta", "Ocaña", "Pamplona", "Villa del Rosario", "Los Patios", "Tibú", "El Zulia", "Chinácota", "Ábrego", "Sardinata", "Toledo", "Convención"],
            "PUTUMAYO": ["Mocoa", "Puerto Asís", "Orito", "Valle del Guamuez (La Hormiga)", "Villagarzón", "Puerto Guzmán", "Sibundoy", "San Francisco", "Colón", "Santiago"],
            "QUINDÍO": ["Armenia", "Calarcá", "La Tebaida", "Montenegro", "Quimbaya", "Circasia", "Filandia", "Salento", "Génova", "Pijao", "Córdoba", "Buenavista"],
            "RISARALDA": ["Pereira", "Dosquebradas", "Santa Rosa de Cabal", "La Virginia", "Belén de Umbría", "Santuario", "Quinchía", "Marsella", "Mistrató", "Guática", "Apía"],
            "SAN ANDRÉS Y PROVIDENCIA": ["San Andrés", "Providencia"],
            "SANTANDER": ["Bucaramanga", "Floridablanca", "Girón", "Piedecuesta", "Barrancabermeja", "San Gil", "Socorro", "Málaga", "Cimitarra", "Barbosa", "Lebrija", "Rionegro", "Sabana de Torres", "Vélez", "Zapatoca", "Barichara", "Charalá", "San Vicente de Chucurí"],
            "SUCRE": ["Sincelejo", "Corozal", "San Marcos", "Tolú", "San Onofre", "Sampués", "Sincé", "Coveñas", "Majagual", "Galeras", "Toluviejo", "San Benito Abad"],
            "TOLIMA": ["Ibagué", "Espinal", "Melgar", "Chaparral", "Mariquita", "Honda", "Líbano", "Flandes", "Fresno", "Guamo", "Purificación", "Saldaña", "Armero Guayabal", "Cajamarca"],
            "VALLE DEL CAUCA": ["Cali", "Buenaventura", "Palmira", "Tuluá", "Yumbo", "Cartago", "Buga", "Jamundí", "Candelaria", "Pradera", "Florida", "Zarzal", "Sevilla", "Roldanillo", "Caicedonia", "Dagua", "Ginebra", "La Unión", "Bugalagrande"],
            "VAUPÉS": ["Mitú", "Carurú", "Taraira", "Papunaua", "Yavaraté", "Pacoa"],
            "VICHADA": ["Puerto Carreño", "La Primavera", "Santa Rosalía", "Cumaribo"]
        };

        // Estado
        let productos = JSON.parse(localStorage.getItem('dst_productos')) || productosPorDefecto;
        let carrito = JSON.parse(localStorage.getItem('carrito')) || [];
        let categoriaActiva = 'todos';

        // Inicialización de Departamentos y Municipios
        function poblarDepartamentosYCiudades() {
            const selectDepto = document.getElementById('departamento');
            const ciudadInput = document.getElementById('ciudad-input');
            const dataList = document.getElementById('lista-ciudades');

            selectDepto.innerHTML = '<option value="">Seleccione un departamento...</option>';
            Object.keys(colombiaCompleta).sort().forEach(depto => {
                const opt = document.createElement('option');
                opt.value = depto;
                opt.textContent = depto;
                selectDepto.appendChild(opt);
            });

            selectDepto.addEventListener('change', function() {
                const depto = this.value;
                dataList.innerHTML = '';
                ciudadInput.value = '';
                
                if (depto && colombiaCompleta[depto]) {
                    ciudadInput.disabled = false;
                    ciudadInput.placeholder = `Escribe o busca un municipio de ${depto}...`;
                    colombiaCompleta[depto].sort().forEach(ciudad => {
                        const opt = document.createElement('option');
                        opt.value = ciudad;
                        dataList.appendChild(opt);
                    });
                } else {
                    ciudadInput.disabled = true;
                    ciudadInput.placeholder = "Seleccione un departamento primero...";
                }
            });
        }

        // Renderizado del Catálogo
        function renderizarProductos(lista) {
            const container = document.getElementById('productos-container');
            if (lista.length === 0) {
                container.innerHTML = '<p style="margin: 40px auto; color: #888;">No se encontraron productos.</p>';
                return;
            }

            container.innerHTML = lista.map(p => {
                const agotado = p.stock === false;
                return `
                    <div class="producto ${agotado ? 'agotado' : ''}">
                        ${agotado ? '<span class="badge-agotado">Agotado</span>' : ''}
                        <img src="${p.img}" alt="${p.nombre}" onclick="ampliarImagen('${p.img}')">
                        <h3>${p.nombre}</h3>
                        <p>${p.descripcion}</p>
                        
                        <div class="variantes-producto">
                            <select id="talla-${p.id}" ${agotado ? 'disabled' : ''}>
                                ${p.tallas.map(t => `<option value="${t}">${t}</option>`).join('')}
                            </select>
                            <select id="color-${p.id}" ${agotado ? 'disabled' : ''}>
                                ${p.colores.map(c => `<option value="${c}">${c}</option>`).join('')}
                            </select>
                        </div>

                        <div class="precio">$${p.precio.toLocaleString('es-CO')}</div>
                        <button class="btn-add" onclick="agregarAlCarritoConVariantes(${p.id})" ${agotado ? 'disabled' : ''}>
                            ${agotado ? 'Agotado' : 'Añadir al carrito'}
                        </button>
                    </div>
                `;
            }).join('');
        }

        function filtrarCategoria(cat) {
            categoriaActiva = cat;
            document.querySelectorAll('.tag-btn').forEach(btn => btn.classList.remove('active'));
            event.target.classList.add('active');
            aplicarFiltros();
        }

        function buscarProductos() {
            aplicarFiltros();
        }

        function aplicarFiltros() {
            const texto = document.getElementById('busqueda-producto').value.toLowerCase().trim();
            const filtrados = productos.filter(p => {
                const coincideCat = categoriaActiva === 'todos' || p.categoria === categoriaActiva;
                const coincideTxt = p.nombre.toLowerCase().includes(texto) || p.descripcion.toLowerCase().includes(texto);
                return coincideCat && coincideTxt;
            });
            renderizarProductos(filtrados);
        }

        // Carrito
        function agregarAlCarritoConVariantes(id) {
            const producto = productos.find(p => p.id === id);
            if (!producto || producto.stock === false) {
                mostrarNotificacion("Este producto se encuentra agotado");
                return;
            }

            const talla = document.getElementById(`talla-${id}`).value;
            const color = document.getElementById(`color-${id}`).value;
            const itemKey = `${id}-${talla}-${color}`;
            const itemExistente = carrito.find(item => item.key === itemKey);

            if (itemExistente) {
                itemExistente.cantidad += 1;
            } else {
                carrito.push({
                    key: itemKey,
                    id: producto.id,
                    nombre: producto.nombre,
                    img: producto.img,
                    precio: producto.precio,
                    talla: talla,
                    color: color,
                    cantidad: 1
                });
            }

            guardarCarrito();
            actualizarCarrito();
            mostrarNotificacion(`"${producto.nombre}" (${talla}, ${color}) añadido`);
        }

        function modificarCantidad(key, cambio) {
            const item = carrito.find(p => p.key === key);
            if (item) {
                item.cantidad += cambio;
                if (item.cantidad <= 0) {
                    carrito = carrito.filter(p => p.key !== key);
                }
                guardarCarrito();
                actualizarCarrito();
            }
        }

        function actualizarCarrito() {
            const totalItems = carrito.reduce((total, item) => total + item.cantidad, 0);
            document.getElementById('carrito-contador').textContent = totalItems;
            
            const carritoItems = document.getElementById('carrito-items');
            if (carrito.length === 0) {
                carritoItems.innerHTML = '<p style="text-align:center; color:#777; margin: 20px 0;">El carrito está vacío</p>';
            } else {
                carritoItems.innerHTML = carrito.map(item => `
                    <div class="carrito-item">
                        <img src="${item.img}" alt="${item.nombre}" class="carrito-item-img">
                        <div class="carrito-item-info">
                            <span class="carrito-item-nombre">${item.nombre}</span>
                            <div class="carrito-item-detalle">Talla: ${item.talla} | Color: ${item.color}</div>
                            <span class="carrito-item-precio">$${item.precio.toLocaleString('es-CO')}</span>
                        </div>
                        <div class="carrito-item-cantidad">
                            <button onclick="modificarCantidad('${item.key}', -1)">-</button>
                            <span>${item.cantidad}</span>
                            <button onclick="modificarCantidad('${item.key}', 1)">+</button>
                        </div>
                        <div class="carrito-item-subtotal">
                            $${(item.precio * item.cantidad).toLocaleString('es-CO')}
                        </div>
                    </div>
                `).join('');
            }

            const total = carrito.reduce((sum, item) => sum + (item.precio * item.cantidad), 0);
            document.getElementById('carrito-total').textContent = total.toLocaleString('es-CO');
            actualizarQRNequi(total.toLocaleString('es-CO'));
        }

        function guardarCarrito() {
            localStorage.setItem('carrito', JSON.stringify(carrito));
        }

        function actualizarQRNequi(monto) {
            const qrImg = document.getElementById('qr-nequi');
            const mensajeQR = `NEQUI: Pagar a ${numeroNequi} por valor de $${monto}`;
            qrImg.src = `https://api.qrserver.com/v1/create-qr-code/?size=180x180&data=${encodeURIComponent(mensajeQR)}`;
        }

        function copiarNequi() {
            navigator.clipboard.writeText(numeroNequi).then(() => {
                mostrarNotificacion("¡Número 3222156178 copiado!");
            }).catch(() => {
                mostrarNotificacion("Número: 3222156178");
            });
        }

        function abrirGuiaTallas() {
            document.getElementById('modalTallas').style.display = 'block';
        }
        function cerrarGuiaTallas() {
            document.getElementById('modalTallas').style.display = 'none';
        }

        function mostrarNotificacion(mensaje) {
            const notificacion = document.createElement('div');
            notificacion.className = 'notificacion';
            notificacion.textContent = mensaje;
            document.body.appendChild(notificacion);
            
            setTimeout(() => {
                notificacion.style.opacity = '0';
                setTimeout(() => notificacion.remove(), 400);
            }, 2500);
        }

        function ampliarImagen(src) {
            const modal = document.createElement('div');
            modal.style.position = 'fixed';
            modal.style.top = '0';
            modal.style.left = '0';
            modal.style.width = '100%';
            modal.style.height = '100%';
            modal.style.backgroundColor = 'rgba(0,0,0,0.85)';
            modal.style.display = 'flex';
            modal.style.justifyContent = 'center';
            modal.style.alignItems = 'center';
            modal.style.zIndex = '3000';
            modal.style.cursor = 'zoom-out';
            
            const img = document.createElement('img');
            img.src = src;
            img.style.maxWidth = '90%';
            img.style.maxHeight = '90%';
            img.style.borderRadius = '10px';
            
            modal.appendChild(img);
            document.body.appendChild(modal);
            modal.addEventListener('click', () => modal.remove());
        }

        // ==========================================
        // PANEL ADMINISTRADOR MANUAL SIN CÓDIGO
        // ==========================================
        function abrirAdmin() {
            const clave = prompt("Introduce la clave de acceso de la tienda:");
            if (clave === "1234") { // Puedes modificar esta clave si lo requieres
                renderizarFormulariosAdmin();
                document.getElementById('admin-panel').style.display = 'block';
            } else if (clave !== null) {
                alert("Clave incorrecta.");
            }
        }

        function cerrarAdmin() {
            document.getElementById('admin-panel').style.display = 'none';
        }

        function renderizarFormulariosAdmin() {
            const box = document.getElementById('admin-lista-productos');
            box.innerHTML = productos.map((p, index) => `
                <div class="admin-item" id="admin-prod-${index}">
                    <div style="display:flex; justify-content:space-between; margin-bottom:8px;">
                        <strong>Producto #${p.id}: ${p.nombre}</strong>
                        <button type="button" class="btn-admin-delete" onclick="eliminarProductoAdmin(${index})">Eliminar</button>
                    </div>
                    <div class="admin-item-grid">
                        <div>
                            <label style="font-size:12px; font-weight:bold;">Nombre del Producto:</label>
                            <input type="text" id="adm-nombre-${index}" value="${p.nombre}">
                        </div>
                        <div>
                            <label style="font-size:12px; font-weight:bold;">Precio ($ COP):</label>
                            <input type="number" id="adm-precio-${index}" value="${p.precio}">
                        </div>
                        <div>
                            <label style="font-size:12px; font-weight:bold;">Categoría:</label>
                            <select id="adm-categoria-${index}">
                                <option value="conjuntos" ${p.categoria === 'conjuntos' ? 'selected' : ''}>Conjuntos</option>
                                <option value="gorros" ${p.categoria === 'gorros' ? 'selected' : ''}>Gorros</option>
                                <option value="calzado" ${p.categoria === 'calzado' ? 'selected' : ''}>Calzado</option>
                                <option value="accesorios" ${p.categoria === 'accesorios' ? 'selected' : ''}>Accesorios</option>
                            </select>
                        </div>
                        <div>
                            <label style="font-size:12px; font-weight:bold;">Estado del Stock:</label>
                            <select id="adm-stock-${index}">
                                <option value="true" ${p.stock !== false ? 'selected' : ''}>Disponible (En Stock)</option>
                                <option value="false" ${p.stock === false ? 'selected' : ''}>Agotado</option>
                            </select>
                        </div>
                        <div style="grid-column: 1 / -1;">
                            <label style="font-size:12px; font-weight:bold;">URL de la Imagen:</label>
                            <input type="text" id="adm-img-${index}" value="${p.img}">
                        </div>
                        <div style="grid-column: 1 / -1;">
                            <label style="font-size:12px; font-weight:bold;">Descripción:</label>
                            <textarea id="adm-desc-${index}" rows="2">${p.descripcion}</textarea>
                        </div>
                        <div>
                            <label style="font-size:12px; font-weight:bold;">Tallas (separadas por coma):</label>
                            <input type="text" id="adm-tallas-${index}" value="${p.tallas.join(', ')}">
                        </div>
                        <div>
                            <label style="font-size:12px; font-weight:bold;">Colores (separados por coma):</label>
                            <input type="text" id="adm-colores-${index}" value="${p.colores.join(', ')}">
                        </div>
                    </div>
                </div>
            `).join('');
        }

        function agregarProductoVacio() {
            const nuevoId = productos.length > 0 ? Math.max(...productos.map(p => p.id)) + 1 : 1;
            productos.unshift({
                id: nuevoId,
                categoria: "conjuntos",
                img: "https://i.imgur.com/fSCPxyu.jpg",
                nombre: "Nuevo Producto Artesanal",
                precio: 25000,
                stock: true,
                descripcion: "Descripción de la prenda tejida.",
                tallas: ["0-3 meses", "3-6 meses"],
                colores: ["Blanco", "Rosa"]
            });
            renderizarFormulariosAdmin();
            mostrarNotificacion("Producto agregado arriba. Configúralo y dale Guardar.");
        }

        function eliminarProductoAdmin(index) {
            if (confirm(`¿Seguro que deseas eliminar "${productos[index].nombre}"?`)) {
                productos.splice(index, 1);
                renderizarFormulariosAdmin();
            }
        }

        function guardarCambiosAdmin() {
            for (let i = 0; i < productos.length; i++) {
                productos[i].nombre = document.getElementById(`adm-nombre-${i}`).value.trim();
                productos[i].precio = parseInt(document.getElementById(`adm-precio-${i}`).value) || 0;
                productos[i].categoria = document.getElementById(`adm-categoria-${i}`).value;
                productos[i].stock = document.getElementById(`adm-stock-${i}`).value === "true";
                productos[i].img = document.getElementById(`adm-img-${i}`).value.trim();
                productos[i].descripcion = document.getElementById(`adm-desc-${i}`).value.trim();
                productos[i].tallas = document.getElementById(`adm-tallas-${i}`).value.split(',').map(s => s.trim()).filter(s => s);
                productos[i].colores = document.getElementById(`adm-colores-${i}`).value.split(',').map(s => s.trim()).filter(s => s);
            }

            localStorage.setItem('dst_productos', JSON.stringify(productos));
            aplicarFiltros();
            cerrarAdmin();
            mostrarNotificacion("¡Cambios guardados con éxito!");
        }

        // Inicialización y Listeners
        document.addEventListener('DOMContentLoaded', () => {
            poblarDepartamentosYCiudades();
            aplicarFiltros();
            actualizarCarrito();

            const radioNequi = document.getElementById('radio-nequi');
            const radioAcordar = document.getElementById('radio-acordar');
            const infoNequi = document.getElementById('info-nequi');

            radioNequi.addEventListener('change', () => infoNequi.style.display = 'block');
            radioAcordar.addEventListener('change', () => infoNequi.style.display = 'none');
        });

        // Controles de visibilidad del carrito
        const iconoCarrito = document.getElementById('carrito-icono');
        const carritoDiv = document.getElementById('carrito-contenido');

        iconoCarrito.addEventListener('click', (e) => {
            e.stopPropagation();
            carritoDiv.style.display = carritoDiv.style.display === 'block' ? 'none' : 'block';
        });

        carritoDiv.addEventListener('click', (e) => {
            e.stopPropagation();
        });

        document.getElementById('vaciar-carrito').addEventListener('click', () => {
            carrito = [];
            guardarCarrito();
            actualizarCarrito();
            mostrarNotificacion('Carrito vaciado');
            carritoDiv.style.display = 'none';
        });

        document.getElementById('comprar-carrito').addEventListener('click', (e) => {
            e.preventDefault();
            if (carrito.length === 0) {
                mostrarNotificacion('El carrito está vacío');
                return;
            }
            document.getElementById('modalCompra').style.display = 'block';
            carritoDiv.style.display = 'none';
        });

        document.getElementById('close-modal').addEventListener('click', () => {
            document.getElementById('modalCompra').style.display = 'none';
        });

        // Formulario de Compra
        document.getElementById('formulario-compra').addEventListener('submit', (e) => {
            e.preventDefault();
            
            const nombre = document.getElementById('nombre-completo').value.trim();
            const celular = document.getElementById('celular').value.trim();
            const email = document.getElementById('email').value.trim();
            const departamento = document.getElementById('departamento').value;
            const ciudad = document.getElementById('ciudad-input').value.trim();
            const direccion = document.getElementById('direccion').value.trim();
            const notas = document.getElementById('notas').value.trim();
            const metodoPago = document.querySelector('input[name="metodo-pago"]:checked').value;
            const refNequi = document.getElementById('comprobante-nequi').value.trim();
            
            const total = carrito.reduce((sum, item) => sum + (item.precio * item.cantidad), 0);

            let texto = `¡Hola! Quiero realizar el siguiente pedido en *Dulces Sueños Tejidos*:\n\n`;
            texto += `*PRODUCTOS SOLICITADOS:*\n`;
            carrito.forEach(item => {
                texto += `• *${item.nombre}* [Talla: ${item.talla} | Color: ${item.color}] x${item.cantidad} - $${(item.precio * item.cantidad).toLocaleString('es-CO')}\n`;
            });
            texto += `\n*TOTAL:* $${total.toLocaleString('es-CO')}\n\n`;
            
            texto += `*MÉTODO DE PAGO:*\n`;
            if (metodoPago === 'nequi') {
                texto += `• Pago por Nequi (${numeroNequi})\n`;
                if (refNequi) texto += `• Comprobante/Ref: ${refNequi}\n`;
            } else {
                texto += `• Por convenir / Efectivo / Transferencia\n`;
            }

            texto += `\n*DATOS DE ENTREGA:*\n`;
            texto += `- Destinatario: ${nombre}\n`;
            texto += `- Celular: ${celular}\n`;
            if (email) texto += `- Correo: ${email}\n`;
            texto += `- Ubicación: ${ciudad}, ${departamento}\n`;
            texto += `- Dirección: ${direccion}\n`;
            if (notas) texto += `- Notas: ${notas}\n`;

            const url = `https://wa.me/573222156178?text=${encodeURIComponent(texto)}`;
            window.open(url, '_blank');
            
            document.getElementById('modalCompra').style.display = 'none';
            mostrarNotificacion('Redirigiendo a WhatsApp...');
        });

        // Cierre general por clic exterior
        window.addEventListener('click', (event) => {
            if (event.target === document.getElementById('modalCompra')) {
                document.getElementById('modalCompra').style.display = 'none';
            }
            if (event.target === document.getElementById('modalTallas')) {
                document.getElementById('modalTallas').style.display = 'none';
            }
            if (carritoDiv.style.display === 'block') {
                carritoDiv.style.display = 'none';
            }
        });
    </script>
</body>
</html>
