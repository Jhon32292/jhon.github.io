<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dulces Sueños Tejidos - Tienda Artesanal</title>
    <style>
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
        }
        .producto:hover {
            transform: translateY(-5px);
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
        }
        .producto .precio {
            font-weight: bold;
            color: #FF6F61;
            font-size: 18px;
            margin: 10px 0;
        }
        .producto button {
            background-color: #FF6F61;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            margin: 5px;
            transition: background-color 0.3s;
            font-weight: bold;
        }
        .producto button:hover {
            background-color: #FF3B2F;
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
            width: 350px;
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            z-index: 100;
            max-height: 80vh;
            overflow-y: auto;
        }
        .carrito-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
            border-bottom: 1px solid #eee;
            padding-bottom: 10px;
        }
        .carrito-item-info {
            flex-grow: 1;
        }
        .carrito-item-cantidad {
            display: flex;
            align-items: center;
            margin: 0 10px;
        }
        .carrito-item-cantidad button {
            background: #87CEEB;
            border: none;
            width: 25px;
            height: 25px;
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
            margin: 0 8px;
            min-width: 20px;
            text-align: center;
        }
        .carrito-item-subtotal {
            min-width: 80px;
            text-align: right;
        }
        .carrito-total {
            font-weight: bold;
            text-align: right;
            margin-top: 15px;
            font-size: 1.2em;
            padding-top: 10px;
            border-top: 2px solid #6B5B95;
        }
        .carrito-acciones {
            display: flex;
            justify-content: space-between;
            margin-top: 15px;
        }
        .carrito-acciones button {
            padding: 10px 15px;
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
            background-color: rgba(0,0,0,0.4);
        }
        .modal-content {
            background-color: #FFF8F0;
            margin: 5% auto;
            padding: 25px;
            border-radius: 10px;
            width: 90%;
            max-width: 500px;
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
            margin-bottom: 15px;
        }
        .form-group label {
            display: block;
            margin-bottom: 5px;
            color: #6B5B95;
            font-weight: bold;
        }
        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-family: 'Arial', sans-serif;
            box-sizing: border-box;
        }
        .form-group input:focus, .form-group select:focus {
            outline: none;
            border-color: #87CEEB;
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
            margin-top: 10px;
        }
        .btn-submit:hover {
            background-color: #FF3B2F;
        }
        /* Notificaciones */
        .notificacion {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: #4CAF50;
            color: white;
            padding: 15px;
            border-radius: 5px;
            z-index: 1000;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
            transition: all 0.5s ease;
        }
        /* Responsive */
        @media (max-width: 900px) {
            .producto {
                width: 45%;
            }
        }
        @media (max-width: 600px) {
            .producto {
                width: 100%;
            }
            .carrito-contenido {
                width: 90%;
                right: 5%;
                left: 5%;
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
                <button id="vaciar-carrito">Vaciar Carrito</button>
                <button id="comprar-carrito">Comprar</button>
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
        <div class="productos" id="productos-container"></div>
    </section>

    <section id="contacto">
        <h2>Contacto</h2>
        <div class="contacto-info">
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

    <!-- Modal de compra -->
    <div id="modalCompra" class="modal">
        <div class="modal-content">
            <span class="close" id="close-modal">&times;</span>
            <h2>Finalizar Compra</h2>
            <form id="formulario-compra">
                <input type="hidden" id="productos-compra" name="productos">
                <input type="hidden" id="total-compra" name="total">
                
                <div class="form-group">
                    <label for="nombre-completo">Nombre y Apellido:</label>
                    <input type="text" id="nombre-completo" name="nombre-completo" required>
                </div>
                
                <div class="form-group">
                    <label for="celular">Celular:</label>
                    <input type="tel" id="celular" name="celular" required>
                </div>
                
                <div class="form-group">
                    <label for="email">Correo Electrónico:</label>
                    <input type="email" id="email" name="email">
                </div>
                
                <div class="form-group">
                    <label for="departamento">Departamento:</label>
                    <select id="departamento" name="departamento" required>
                        <option value="">Seleccione un departamento</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="ciudad">Ciudad/Municipio:</label>
                    <select id="ciudad" name="ciudad" required disabled>
                        <option value="">Primero seleccione un departamento</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="direccion">Dirección completa:</label>
                    <textarea id="direccion" name="direccion" rows="3" required></textarea>
                </div>
                
                <div class="form-group">
                    <label for="notas">Notas adicionales:</label>
                    <textarea id="notas" name="notas" rows="2"></textarea>
                </div>
                
                <button type="submit" class="btn-submit">Enviar Pedido por WhatsApp</button>
            </form>
        </div>
    </div>

    <!-- Botón de WhatsApp flotante -->
    <a href="https://wa.me/573222156178" class="whatsapp" target="_blank" title="Contactar por WhatsApp">
        <img src="https://upload.wikimedia.org/wikipedia/commons/6/6b/WhatsApp.svg" alt="WhatsApp" width="30">
    </a>

    <footer>
        <p>© 2023 Dulces Sueños Tejidos - Todos los derechos reservados</p>
    </footer>

    <script>
        // Datos de productos
        const productos = [
            { 
                id: 1, 
                img: "https://i.imgur.com/fSCPxyu.jpg", 
                nombre: "Saco y manopla para bebé", 
                precio: 35000, 
                descripcion: "Conjunto práctico y adorable diseñado para mantener a tu pequeño abrigado y cómodo. Hecho con lana suave hipoalergénica." 
            },
            { 
                id: 2, 
                img: "https://i.imgur.com/aFgxCzQ.jpg", 
                nombre: "Conjunto completo 4 x 1", 
                precio: 60000, 
                descripcion: "La combinación perfecta de estilo, comodidad y funcionalidad para tu bebé. Incluye gorro, saco, patines y manoplas." 
            },
            { 
                id: 3, 
                img: "https://i.imgur.com/uRAX5jA.jpg", 
                nombre: "Esquimal para bebé", 
                precio: 40000, 
                descripcion: "¡Abraza la ternura y el estilo invernal con este adorable conjunto esquimal! Ideal para días fríos y sesiones de fotos." 
            },
            { 
                id: 4, 
                img: "https://i.imgur.com/tiJobRZ.jpg", 
                nombre: "Zapatitos tejidos", 
                precio: 15000, 
                descripcion: "Estos zapatitos para bebé son la combinación perfecta de ternura, comodidad y estilo. Disponibles en varios colores." 
            },
            { 
                id: 5, 
                img: "https://i.imgur.com/CVD60u3.jpg", 
                nombre: "Moños para el cabello", 
                precio: 10000, 
                descripcion: "¡Añade un toque de dulzura y estilo al look de tu pequeña! Ideales para ocasiones especiales o uso diario." 
            },
            { 
                id: 6, 
                img: "https://i.imgur.com/dFqY8Fs.jpg", 
                nombre: "Apliques (Paquete x 6)", 
                precio: 10000, 
                descripcion: "Dale un toque único y personalizado a las prendas de tu bebé con este encantador paquete de apliques en lana." 
            },
            { 
                id: 7, 
                img: "https://i.imgur.com/CcRs4h4.jpg", 
                nombre: "Gorros para bebés", 
                precio: 25000, 
                descripcion: "Mantén la cabecita de tu bebé abrigada y con estilo con estos adorables gorros. Disponibles en diversos diseños." 
            },
            { 
                id: 8, 
                img: "https://i.imgur.com/eDyzLbd.jpg", 
                nombre: "Gorros doble faz", 
                precio: 25000, 
                descripcion: "Descubre la versatilidad y el estilo con estos prácticos y encantadores gorros doble faz para bebé." 
            }
        ];

        // Datos de departamentos y municipios
        const departamentosYCiudades = {
            "Amazonas": ["Leticia", "Puerto Nariño"],
            "Antioquia": ["Medellín", "Bello", "Itagüí", "Envigado"],
            "Arauca": ["Arauca", "Saravena"],
            "Atlántico": ["Barranquilla", "Soledad", "Malambo"],
            "Bogotá, D.C.": ["Bogotá"],
            "Bolívar": ["Cartagena", "Magangué"],
            "Boyacá": ["Tunja", "Duitama", "Sogamoso", "Soatá"],
            "Caldas": ["Manizales", "La Dorada"],
            "Caquetá": ["Florencia"],
            "Casanare": ["Yopal"],
            "Cauca": ["Popayán"],
            "Cesar": ["Valledupar"],
            "Chocó": ["Quibdó"],
            "Córdoba": ["Montería"],
            "Cundinamarca": ["Soacha", "Girardot"],
            "Guainía": ["Inírida"],
            "Guaviare": ["San José del Guaviare"],
            "Huila": ["Neiva"],
            "La Guajira": ["Riohacha"],
            "Magdalena": ["Santa Marta"],
            "Meta": ["Villavicencio"],
            "Nariño": ["Pasto"],
            "Norte de Santander": ["Cúcuta"],
            "Putumayo": ["Mocoa"],
            "Quindío": ["Armenia"],
            "Risaralda": ["Pereira"],
            "San Andrés": ["San Andrés"],
            "Santander": ["Bucaramanga"],
            "Sucre": ["Sincelejo"],
            "Tolima": ["Ibagué"],
            "Valle del Cauca": ["Cali"],
            "Vaupés": ["Mitú"],
            "Vichada": ["Puerto Carreño"]
        };

        // Carrito (carga desde localStorage si existe)
        let carrito = JSON.parse(localStorage.getItem('carrito')) || [];

        // Mostrar productos en el catálogo
        function mostrarProductos() {
            const container = document.getElementById('productos-container');
            container.innerHTML = productos.map(producto => `
                <div class="producto">
                    <img src="${producto.img}" alt="${producto.nombre}" onclick="ampliarImagen('${producto.img}')">
                    <h3>${producto.nombre}</h3>
                    <p>${producto.descripcion}</p>
                    <div class="precio">$${producto.precio.toLocaleString()}</div>
                    <button onclick="agregarAlCarrito(${producto.id})">Añadir al carrito</button>
                </div>
            `).join('');
        }

        // Funciones del carrito
        function agregarAlCarrito(id) {
            const producto = productos.find(p => p.id === id);
            const itemExistente = carrito.find(item => item.id === id);
            
            if (itemExistente) {
                itemExistente.cantidad += 1;
            } else {
                carrito.push({ ...producto, cantidad: 1 });
            }
            
            guardarCarrito();
            actualizarCarrito();
            mostrarNotificacion(`${producto.nombre} añadido al carrito`);
        }

        function modificarCantidad(id, cambio) {
            const item = carrito.find(item => item.id === id);
            if (item) {
                item.cantidad += cambio;
                
                if (item.cantidad <= 0) {
                    carrito = carrito.filter(item => item.id !== id);
                }
                
                guardarCarrito();
                actualizarCarrito();
            }
        }

        function actualizarCarrito() {
            // Actualizar contador
            const totalItems = carrito.reduce((total, item) => total + item.cantidad, 0);
            document.getElementById('carrito-contador').textContent = totalItems;
            
            // Actualizar items del carrito
            const carritoItems = document.getElementById('carrito-items');
            carritoItems.innerHTML = carrito.map(item => `
                <div class="carrito-item">
                    <div class="carrito-item-info">
                        <strong>${item.nombre}</strong>
                        <div>$${item.precio.toLocaleString()} c/u</div>
                    </div>
                    <div class="carrito-item-cantidad">
                        <button onclick="modificarCantidad(${item.id}, -1)">-</button>
                        <span>${item.cantidad}</span>
                        <button onclick="modificarCantidad(${item.id}, 1)">+</button>
                    </div>
                    <div class="carrito-item-subtotal">
                        $${(item.precio * item.cantidad).toLocaleString()}
                    </div>
                </div>
            `).join('');

            // Actualizar total
            const total = carrito.reduce((sum, item) => sum + (item.precio * item.cantidad), 0);
            document.getElementById('carrito-total').textContent = total.toLocaleString();
            
            // Actualizar datos para el formulario de compra
            document.getElementById('productos-compra').value = JSON.stringify(carrito);
            document.getElementById('total-compra').value = total;
        }

        function guardarCarrito() {
            localStorage.setItem('carrito', JSON.stringify(carrito));
        }

        // Funciones para el modal de compra
        function llenarDepartamentos() {
            const selectDepto = document.getElementById('departamento');
            selectDepto.innerHTML = '<option value="">Seleccione un departamento</option>';
            
            Object.keys(departamentosYCiudades).forEach(depto => {
                const option = document.createElement('option');
                option.value = depto;
                option.textContent = depto;
                selectDepto.appendChild(option);
            });
        }

        function configurarCiudades() {
            const selectDepto = document.getElementById('departamento');
            const selectCiudad = document.getElementById('ciudad');
            
            selectDepto.addEventListener('change', function() {
                const depto = this.value;
                selectCiudad.innerHTML = '<option value="">Seleccione una ciudad</option>';
                selectCiudad.disabled = !depto;
                
                if (depto) {
                    departamentosYCiudades[depto].forEach(ciudad => {
                        const option = document.createElement('option');
                        option.value = ciudad;
                        option.textContent = ciudad;
                        selectCiudad.appendChild(option);
                    });
                }
            });
        }

        // Notificaciones
        function mostrarNotificacion(mensaje) {
            const notificacion = document.createElement('div');
            notificacion.className = 'notificacion';
            notificacion.textContent = mensaje;
            
            document.body.appendChild(notificacion);
            
            setTimeout(() => {
                notificacion.style.opacity = '0';
                setTimeout(() => document.body.removeChild(notificacion), 500);
            }, 3000);
        }

        // Ampliar imagen
        function ampliarImagen(src) {
            const modal = document.createElement('div');
            modal.style.position = 'fixed';
            modal.style.top = '0';
            modal.style.left = '0';
            modal.style.width = '100%';
            modal.style.height = '100%';
            modal.style.backgroundColor = 'rgba(0,0,0,0.8)';
            modal.style.display = 'flex';
            modal.style.justifyContent = 'center';
            modal.style.alignItems = 'center';
            modal.style.zIndex = '1000';
            modal.style.cursor = 'zoom-out';
            
            const img = document.createElement('img');
            img.src = src;
            img.style.maxWidth = '90%';
            img.style.maxHeight = '90%';
            img.style.borderRadius = '10px';
            
            modal.appendChild(img);
            document.body.appendChild(modal);
            
            modal.addEventListener('click', () => {
                document.body.removeChild(modal);
            });
        }

        // Eventos
        document.addEventListener('DOMContentLoaded', () => {
            mostrarProductos();
            actualizarCarrito();
            llenarDepartamentos();
            configurarCiudades();
        });

        document.getElementById('carrito-icono').addEventListener('click', () => {
            const carritoDiv = document.getElementById('carrito-contenido');
            carritoDiv.style.display = carritoDiv.style.display === 'block' ? 'none' : 'block';
        });

        document.getElementById('vaciar-carrito').addEventListener('click', () => {
            carrito = [];
            guardarCarrito();
            actualizarCarrito();
            mostrarNotificacion('Carrito vaciado');
            document.getElementById('carrito-contenido').style.display = 'none';
        });

        document.getElementById('comprar-carrito').addEventListener('click', (e) => {
            e.preventDefault();
            if (carrito.length === 0) {
                mostrarNotificacion('El carrito está vacío');
                return;
            }
            document.getElementById('modalCompra').style.display = 'block';
            document.getElementById('carrito-contenido').style.display = 'none';
        });

        document.getElementById('close-modal').addEventListener('click', () => {
            document.getElementById('modalCompra').style.display = 'none';
        });

        document.getElementById('formulario-compra').addEventListener('submit', (e) => {
            e.preventDefault();
            
            const nombre = document.getElementById('nombre-completo').value;
            const celular = document.getElementById('celular').value;
            const departamento = document.getElementById('departamento').value;
            const ciudad = document.getElementById('ciudad').value;
            const direccion = document.getElementById('direccion').value;
            const email = document.getElementById('email').value;
            const notas = document.getElementById('notas').value;
            
            // Crear mensaje para WhatsApp
            let mensaje = `¡Hola! Quiero realizar la siguiente compra:%0A%0A`;
            
            carrito.forEach(item => {
                mensaje += `*${item.nombre}* - Cantidad: ${item.cantidad} - $${item.precio.toLocaleString()} c/u%0A`;
            });
            
            mensaje += `%0A*Total:* $${document.getElementById('total-compra').value}%0A%0A`;
            mensaje += `*Mis datos:*%0A`;
            mensaje += `- Nombre: ${nombre}%0A`;
            mensaje += `- Celular: ${celular}%0A`;
            if (email) mensaje += `- Email: ${email}%0A`;
            mensaje += `- Departamento: ${departamento}%0A`;
            mensaje += `- Ciudad: ${ciudad}%0A`;
            mensaje += `- Dirección: ${direccion}%0A`;
            if (notas) mensaje += `%0A*Notas:* ${notas}%0A`;
            
            // Redirigir a WhatsApp
            window.open(`https://wa.me/573222156178?text=${mensaje}`, '_blank');
            
            // Opcional: vaciar carrito después de comprar
            // carrito = [];
            // guardarCarrito();
            // actualizarCarrito();
            
            document.getElementById('modalCompra').style.display = 'none';
            mostrarNotificacion('Pedido enviado por WhatsApp');
        });

        // Cerrar modal al hacer clic fuera
        window.addEventListener('click', (event) => {
            if (event.target === document.getElementById('modalCompra')) {
                document.getElementById('modalCompra').style.display = 'none';
            }
            if (event.target === document.getElementById('carrito-contenido')) {
                document.getElementById('carrito-contenido').style.display = 'none';
            }
        });
    </script>
</body>
</html>

