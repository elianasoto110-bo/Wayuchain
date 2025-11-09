<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>WayuChain - Blockchain PoC (Roles y Permisos)</title>
    <!-- Carga de Tailwind CSS para un estilo moderno y responsive -->
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        /* Estilos personalizados para el proyecto */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f7f9fb; /* Fondo muy claro */
        }
        .guajira-gradient {
            /* Degradado que evoca los tonos cálidos de la arena de La Guajira (Dorado y Ocre) */
            background: linear-gradient(135deg, #B8860B 0%, #FFD700 100%); 
        }
        .card {
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
        }
        .btn-primary {
            transition: all 0.2s;
        }
        .btn-primary:hover {
            transform: translateY(-1px);
            /* Sombra ajustada al nuevo color de la arena */
            box-shadow: 0 4px 10px rgba(184, 134, 11, 0.4); 
        }
        .login-container {
            min-height: 100vh;
        }
        /* imagen de bombillo con el fondo del mapa de colombia en colores vivos*/
     
     .chain-icon {
            display: inline-block;
            width: 1.25rem;
            height: 1.25rem;
            background-color: currentColor;
            mask: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24'%3E%3Cpath d='M17.5 14h-2.5v-2h2.5c2.21 0 4-1.79 4-4s-1.79-4-4-4h-5c-2.21 0-4 1.79-4 4s1.79 4 4 4h.5v2h-.5c-3.31 0-6-2.69-6-6s2.69-6 6-6h5c3.31 0 6 2.69 6 6s-2.69 6-6 6zm-5 4h-2.5v-2h2.5c2.21 0 4-1.79 4-4s-1.79-4-4-4h-5c-2.21 0-4 1.79-4 4s1.79 4 4 4h-.5v2h.5c3.31 0 6-2.69 6-6s-2.69-6-6-6h-5c-3.31 0-6 2.69-6 6s2.69 6 6 6z'/%3E%3C/svg%3E") no-repeat center;
            -webkit-mask: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24'%3E%3Cpath d='M17.5 14h-2.5v-2h2.5c2.21 0 4-1.79 4-4s-1.79-4-4-4h-5c-2.21 0-4 1.79-4 4s1.79 4 4 4h.5v2h-.5c-3.31 0-6-2.69-6-6s2.69-6 6-6h5c3.31 0 6 2.69 6 6s-2.69 6-6 6zm-5 4h-2.5v-2h2.5c2.21 0 4-1.79 4-4s-1.79-4-4-4h-5c-2.21 0-4 1.79-4 4s1.79 4 4 4h-.5v2h.5c3.31 0 6-2.69 6-6s-2.69-6-6-6h-5c-3.31 0-6 2.69-6 6s2.69 6 6 6z'/%3E%3C/svg%3E") no-repeat center;
        }
        /* Icono de Wallet */
        .wallet-icon {
            display: inline-block;
            width: 1.25rem;
            height: 1.25rem;
            background-color: currentColor;
            mask: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24'%3E%3Cpath d='M21 18V6c0-1.1-.9-2-2-2H5c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2zm-9-7c-1.66 0-3-1.34-3-3s1.34-3 3-3 3 1.34 3 3-1.34 3-3 3z'/%3E%3C/svg%3E") no-repeat center;
            -webkit-mask: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24'%3E%3Cpath d='M21 18V6c0-1.1-.9-2-2-2H5c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2zm-9-7c-1.66 0-3-1.34-3-3s1.34-3 3-3 3 1.34 3 3-1.34 3-3 3z'/%3E%3C/svg%3E") no-repeat center;
        }
    </style>
</head>
<body>

<!-- Contenedor Principal de la Aplicación -->
<div id="app" class="relative">

    <!-- Pantalla de Login -->
    <section id="login-screen" class="login-container flex items-center justify-center p-4">
        <div class="w-full max-w-lg card bg-white rounded-xl overflow-hidden shadow-2xl">
            <!-- Encabezado con branding -->
            <div class="guajira-gradient p-8 text-white">
                <div class="flex items-center space-x-2 mb-2">
                    <span class="chain-icon text-white"></span>
                    <h1 class="text-3xl font-bold">WayuChain</h1>
                </div>
                <p class="text-lg font-light">Energía que Ilumina Confianza</p>
            </div>

            <!-- Formulario de Login -->
            <div class="p-8">
                <h2 class="text-xl font-semibold mb-6 text-gray-800">Inicio de Sesión</h2>

                <!-- Selector de Rol (Simulación de diferentes actores) -->
                <div class="mb-6">
                    <label for="role-select" class="block text-sm font-medium text-gray-700 mb-2">Selecciona tu Rol:</label>
                    <select id="role-select" class="mt-1 block w-full pl-3 pr-10 py-3 text-base border-gray-300 focus:outline-none focus:ring-emerald-500 focus:border-emerald-500 sm:text-sm rounded-lg border">
                        <option value="financiador">Financiador (World Bank)</option>
                        <option value="ejecutor">Organización Ejecutora (Talento Tech)</option>
                        <option value="validador">Validador Comunitario (Líder Wayuu)</option>
                        <option value="publico">Acceso Público (Solo Vista)</option>
                    </select>
                </div>

                <!-- Campo de Usuario (simulado) -->
                <div class="mb-4">
                    <label for="username" class="block text-sm font-medium text-gray-700 mb-2">Usuario (E-mail o ID):</label>
                    <input type="text" id="username" value="demo@guajira.com"
                           class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-emerald-500 focus:border-emerald-500 transition duration-150"
                           placeholder="Ingresa tu usuario">
                </div>

                <!-- Campo de Contraseña (simulado) -->
                <div class="mb-6">
                    <label for="password" class="block text-sm font-medium text-gray-700 mb-2">Contraseña (Simulada):</label>
                    <input type="password" id="password" value="123456"
                           class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-emerald-500 focus:border-emerald-500 transition duration-150"
                           placeholder="Ingresa tu contraseña">
                </div>

                <button onclick="login()"
                        class="btn-primary w-full py-3 rounded-xl text-white font-semibold guajira-gradient">
                    <span class="chain-icon mr-2"></span> Entrar a la Plataforma
                </button>

                <p class="text-center text-sm text-gray-500 mt-6">
                    <a href="#" class="text-emerald-600 hover:text-emerald-800">¿Olvidaste tu contraseña?</a>
                </p>
            </div>
        </div>
    </section>

    <!-- Pantalla del Dashboard (Inicialmente oculta) -->
    <section id="dashboard-screen" class="hidden min-h-screen p-4 lg:p-8 bg-gray-50">
        <!-- Barra de Navegación del Dashboard -->
        <header class="bg-white rounded-xl shadow-lg p-4 mb-8 flex flex-col md:flex-row justify-between items-center">
            <div class="flex items-center space-x-3">
                <!-- Usamos un tono verde-esmeralda para el ícono por contraste visual en el dashboard, aunque el gradiente sea arena -->
                <span class="chain-icon text-emerald-600 w-6 h-6"></span> 
                <h1 class="text-2xl font-bold text-gray-800">Panel de Trazabilidad</h1>
            </div>
            <div class="mt-4 md:mt-0 flex items-center space-x-4">
                <span id="welcome-user" class="text-lg font-semibold text-emerald-600"></span>
                <button onclick="logout()"
                        class="bg-gray-200 hover:bg-gray-300 text-gray-700 font-medium py-2 px-4 rounded-xl transition duration-150">
                    Cerrar Sesión
                </button>
            </div>
        </header>

        <!-- Contenido Principal: Resumen del Proyecto y Hitos -->
        <main>
            <h2 class="text-3xl font-extrabold text-gray-900 mb-6">Proyecto: Electrificación Sostenible La Guajira</h2>
            
            <!-- Grid de Wallet y Métricas Clave -->
            <div class="grid grid-cols-1 lg:grid-cols-4 gap-6 mb-8">
                
                <!-- Columna de Wallet Simulada (2/4 de ancho en desktop) -->
                <div class="lg:col-span-2 bg-white card p-6 rounded-xl border-t-4 border-emerald-500">
                    <div class="flex items-center justify-between mb-3">
                        <h3 class="text-xl font-bold text-gray-800 flex items-center">
                            <span class="wallet-icon mr-2 text-emerald-600"></span>
                            Wallet Simulada
                        </h3>
                        <!-- Etiqueta de Rol actual en la Wallet -->
                        <span id="wallet-role-tag" class="text-xs font-semibold px-3 py-1 rounded-full bg-emerald-100 text-emerald-800"></span>
                    </div>

                    <p class="text-sm font-medium text-gray-500">Dirección Pública (Ficticia)</p>
                    <p class="text-base font-mono text-gray-700 break-all mt-1" id="wallet-address">0x0000...0000</p>
                    
                    <div class="mt-4 pt-4 border-t border-gray-100">
                        <p class="text-sm font-medium text-gray-500">Saldo Disponible (USD Simulado)</p>
                        <p class="text-4xl font-extrabold text-emerald-600 mt-1" id="wallet-balance">$ 0.00</p>
                    </div>
                </div>

                <!-- Métricas 2 y 3 (1/4 de ancho cada una en desktop) -->
                <div class="lg:col-span-2 grid grid-cols-1 sm:grid-cols-2 gap-6">
                    <!-- Métrica 1: Fondos Desembolsados -->
                    <div class="bg-white card p-6 rounded-xl border-t-4 border-yellow-500">
                        <p class="text-sm font-medium text-gray-500">Fondos Desembolsados</p>
                        <p class="text-3xl font-bold text-gray-900 mt-1" id="disbursed-funds">$ 500.000 USD</p>
                        <p class="text-xs text-gray-500 mt-2">Liberados tras Validación de Hitos</p>
                    </div>
                    <!-- Métrica 2: Porcentaje de Hitos Validados -->
                    <div class="bg-white card p-6 rounded-xl border-t-4 border-blue-500">
                        <p class="text-sm font-medium text-gray-500">Hitos Técnicos Validados</p>
                        <p class="text-3xl font-bold text-gray-900 mt-1">4 de 12 (33%)</p>
                        <p class="text-xs text-gray-500 mt-2">Registrado Inmutablemente en Blockchain</p>
                    </div>
                </div>
            </div>

            <!-- Tabla de Trazabilidad de Hitos (Componente Central) -->
            <div class="bg-white card rounded-xl p-6 mb-8">
                <h3 class="text-xl font-semibold text-gray-800 mb-4 flex items-center">
                    <span class="chain-icon text-gray-600 mr-2"></span>
                    Trazabilidad Detallada por Hito
                </h3>
                <div class="overflow-x-auto">
                    <table class="min-w-full divide-y divide-gray-200">
                        <thead class="bg-gray-50">
                            <tr>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Hito</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Monto (USD)</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Evidencia CID</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Estado</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Acciones</th>
                            </tr>
                        </thead>
                        <tbody class="bg-white divide-y divide-gray-200">
                            <!-- Hito 1: COMPLETADO -->
                            <tr class="hover:bg-green-50/50 transition duration-100">
                                <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">1. Compra de Paneles Solares</td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">$ 150.000</td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm text-blue-600 font-mono overflow-ellipsis overflow-hidden max-w-xs">Qmesv...p8f</td>
                                <td class="px-6 py-4 whitespace-nowrap">
                                    <span class="px-2 inline-flex text-xs leading-5 font-semibold rounded-full bg-green-100 text-green-800">VALIDADO</span>
                                </td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm font-medium">
                                    <a href="#" class="text-emerald-600 hover:text-emerald-900 disabled:text-gray-400 disabled:cursor-not-allowed" title="Ver Transacción en Explorador">Ver Tx</a>
                                </td>
                            </tr>
                            <!-- Hito 2: PENDIENTE DE VALIDACIÓN -->
                            <tr class="hover:bg-yellow-50/50 transition duration-100" id="hito2-row">
                                <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">2. Transporte y Logística (Anticipo)</td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">$ 50.000</td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm text-blue-600 font-mono overflow-ellipsis overflow-hidden max-w-xs">Qmkh...y0t</td>
                                <td class="px-6 py-4 whitespace-nowrap">
                                    <span class="px-2 inline-flex text-xs leading-5 font-semibold rounded-full bg-yellow-100 text-yellow-800" id="hito2-status">EN REVISIÓN</span>
                                </td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm font-medium">
                                    <!-- Permiso: Solo Validador -->
                                    <button onclick="openMilestoneModal(2, 'validador')" id="hito2-action"
                                        class="text-blue-600 hover:text-blue-900 disabled:text-gray-400 disabled:cursor-not-allowed" title="Validar Evidencias">Validar</button>
                                </td>
                            </tr>
                            <!-- Hito 3: PENDIENTE DE EJECUCIÓN -->
                            <tr class="hover:bg-gray-50 transition duration-100" id="hito3-row">
                                <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">3. Instalación de la Primera Torre</td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">$ 200.000</td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-400 font-mono" id="hito3-cid-display">N/A</td>
                                <td class="px-6 py-4 whitespace-nowrap">
                                    <span class="px-2 inline-flex text-xs leading-5 font-semibold rounded-full bg-gray-100 text-gray-800" id="hito3-status">PENDIENTE</span>
                                </td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm font-medium">
                                    <!-- Permiso: Solo Ejecutor -->
                                    <button onclick="openMilestoneModal(3, 'ejecutor')" id="hito3-action"
                                        class="text-emerald-600 hover:text-emerald-900 disabled:text-gray-400 disabled:cursor-not-allowed" title="Subir Evidencias">Subir Evidencias</button>
                                </td>
                            </tr>
                            <!-- Hito 4: PENDIENTE (Siguiente fase) -->
                            <tr>
                                <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">4. Capacitación Comunitaria</td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">$ 25.000</td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-400 font-mono">N/A</td>
                                <td class="px-6 py-4 whitespace-nowrap">
                                    <span class="px-2 inline-flex text-xs leading-5 font-semibold rounded-full bg-gray-100 text-gray-800">PENDIENTE</span>
                                </td>
                                <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-400">N/A</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
                <!-- Mensaje de Rol para la Audiencia -->
                <div class="mt-6 p-4 bg-emerald-50 border border-emerald-200 rounded-lg text-sm text-emerald-800">
                    <p class="font-semibold">Información del Rol y Permisos:</p>
                    <p id="role-info">Has iniciado sesión. Utiliza el selector de rol en el login para ver cómo la interfaz cambia.</p>
                </div>
            </div>

            <!-- Historial de Acciones (Blockchain Transactions) -->
            <div class="bg-white card rounded-xl p-6">
                <h3 class="text-xl font-semibold text-gray-800 mb-4 flex items-center">
                    <span class="chain-icon text-gray-600 mr-2"></span>
                    Historial de Acciones (Blockchain)
                </h3>
                <div class="overflow-x-auto max-h-96">
                    <ul class="space-y-4 text-sm" id="transaction-history">
                        <!-- Las transacciones se agregarán aquí dinámicamente -->
                        <li class="p-3 bg-gray-50 rounded-lg border-l-4 border-emerald-500">
                            <p class="font-semibold text-gray-800">Transferencia Inicial de Fondos</p>
                            <p class="text-xs text-gray-500">Fecha: 2025-10-01 | Evento: FundDeposited | Tx Hash: <span class="text-blue-500">0x1A2B...C3D4</span></p>
                            <p class="text-xs text-gray-700">Monto: $ 2.000.000 USD | Actor: Financiador</p>
                        </li>
                        <li class="p-3 bg-gray-50 rounded-lg border-l-4 border-green-500">
                            <p class="font-semibold text-gray-800">Hito 1: Compra de Paneles Solares VALIDADO</p>
                            <p class="text-xs text-gray-500">Fecha: 2025-10-15 | Evento: MilestoneValidated | Tx Hash: <span class="text-blue-500">0xEEFF...3456</span></p>
                            <p class="text-xs text-gray-700">Monto Liberado: $ 150.000 USD | Actor: Validador Comunitario</p>
                        </li>
                        <li class="p-3 bg-gray-50 rounded-lg border-l-4 border-yellow-500">
                            <p class="font-semibold text-gray-800">Hito 2: Evidencias de Transporte Subidas</p>
                            <p class="text-xs text-gray-500">Fecha: 2025-11-05 | Evento: MilestoneSubmitted | Tx Hash: <span class="text-blue-500">0x7890...ABCD</span></p>
                            <p class="text-xs text-gray-700">Evidencia CID: Qmkh...y0t | Actor: Ejecutor</p>
                        </li>
                    </ul>
                </div>
            </div>

        </main>
    </section>

    <!-- Modal para Interacción Principal (Validación/Ejecución de Hito) -->
    <div id="milestone-modal" class="fixed inset-0 bg-gray-900 bg-opacity-75 hidden items-center justify-center p-4 z-50 transition-opacity duration-300">
        <div class="bg-white rounded-xl shadow-2xl w-full max-w-xl p-6 relative">
            
            <h3 class="text-2xl font-bold text-gray-800 mb-4" id="modal-title">Detalle del Hito</h3>
            <button onclick="closeMilestoneModal()" class="absolute top-4 right-4 text-gray-400 hover:text-gray-600">
                <!-- Icono X -->
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
            </button>

            <!-- Contenido Dinámico de la Modal -->
            <div id="modal-content-container">
                <!-- Información del Hito Actual -->
                <div class="bg-gray-50 p-4 rounded-lg mb-4">
                    <p class="text-sm font-medium text-gray-500">Hito:</p>
                    <p class="text-lg font-semibold text-gray-800" id="current-hito-name">Nombre del Hito</p>
                    <p class="text-sm font-medium text-gray-500 mt-2">Monto a Desembolsar:</p>
                    <p class="text-xl font-bold text-emerald-600" id="current-hito-amount">$ 0.00 USD</p>
                </div>

                <!-- Formulario/Acciones para Validador -->
                <div id="validador-form" class="hidden">
                    <p class="mb-3 text-gray-700">Como **Validador Comunitario**, revisa la evidencia (`CID`) y confirma que el trabajo ha sido realizado para liberar los fondos.</p>
                    <div class="mb-4">
                        <label class="block text-sm font-medium text-gray-700 mb-2">Evidencia Subida (CID):</label>
                        <a href="#" target="_blank" id="validador-cid" class="text-blue-600 hover:text-blue-800 underline font-mono">Qmkh...y0t (Ver en IPFS)</a>
                    </div>
                    
                    <button onclick="performValidation(true)"
                            class="w-full py-3 rounded-xl text-white font-semibold bg-emerald-600 hover:bg-emerald-700 transition duration-150 mb-2">
                        <span class="chain-icon mr-2 text-white"></span> APROBAR Y LIBERAR FONDOS
                    </button>
                    <button onclick="performValidation(false)"
                            class="w-full py-3 rounded-xl text-gray-700 font-semibold bg-gray-200 hover:bg-gray-300 transition duration-150">
                        RECHAZAR HITO
                    </button>
                </div>

                <!-- Formulario/Acciones para Ejecutor -->
                <div id="ejecutor-form" class="hidden">
                    <p class="mb-3 text-gray-700">Como **Organización Ejecutora**, sube la prueba de la finalización del hito para que el Validador pueda aprobar el desembolso.</p>
                    <div class="mb-4">
                        <label for="new-cid" class="block text-sm font-medium text-gray-700 mb-2">Nuevo CID de Evidencia (Simulación de Archivo):</label>
                        <input type="text" id="new-cid" value="Qme3d1pP...L3sV6a"
                           class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-emerald-500 focus:border-emerald-500 transition duration-150"
                           placeholder="Ej. Qm... (Hash de la evidencia en IPFS)">
                    </div>
                    
                    <button onclick="performExecutionSubmit()"
                            class="w-full py-3 rounded-xl text-white font-semibold guajira-gradient transition duration-150">
                        <span class="chain-icon mr-2 text-white"></span> SUBIR EVIDENCIAS (Registrar en Blockchain)
                    </button>
                </div>
            </div>

            <!-- Contenedor para el mensaje de Alerta (Reemplaza alert()) -->
            <div id="notification-area" class="mt-4 p-3 bg-red-100 text-red-700 rounded-lg hidden"></div>

        </div>
    </div>
</div>

<script>
    // Variables globales
    const loginScreen = document.getElementById('login-screen');
    const dashboardScreen = document.getElementById('dashboard-screen');
    const welcomeUser = document.getElementById('welcome-user');
    const roleInfo = document.getElementById('role-info');
    const milestoneModal = document.getElementById('milestone-modal');
    const transactionHistoryList = document.getElementById('transaction-history');
    const walletAddressElement = document.getElementById('wallet-address');
    const walletBalanceElement = document.getElementById('wallet-balance');
    const walletRoleTagElement = document.getElementById('wallet-role-tag');
    const disbursedFundsElement = document.getElementById('disbursed-funds');
    const notificationArea = document.getElementById('notification-area');
    
    let currentRole = 'publico';
    let currentMilestoneId = null;
    let disbursedFunds = 500000; // Saldo inicial de fondos desembolsados (para las métricas)

    // Simulación de saldos y direcciones por rol
    const actorWallets = {
        financiador: { address: '0xDeaDBeeF00d...C0FFEE', balance: 5000000.00 }, // Gran saldo
        ejecutor: { address: '0x1A2B3C4D5E6F...7890AB', balance: 10000.00 }, // Balance operativo
        validador: { address: '0xBCC99002211A...00C123', balance: 500.00 }, // Pequeño saldo/Incentivo
        publico: { address: '0x000000000000...000000', balance: 0.00 } // Sin wallet activa
    };

    let milestones = {
        1: { name: '1. Compra de Paneles Solares', amount: 150000, displayAmount: '$ 150.000', cid: 'Qmesv...p8f', status: 'VALIDADO', isCompleted: true, actionElement: null, statusElement: null, cidDisplayElement: null, requiredRole: 'publico' },
        2: { name: '2. Transporte y Logística (Anticipo)', amount: 50000, displayAmount: '$ 50.000', cid: 'Qmkh...y0t', status: 'EN REVISIÓN', isCompleted: false, actionElement: null, statusElement: null, cidDisplayElement: null, requiredRole: 'validador' },
        3: { name: '3. Instalación de la Primera Torre', amount: 200000, displayAmount: '$ 200.000', cid: 'N/A', status: 'PENDIENTE', isCompleted: false, actionElement: null, statusElement: null, cidDisplayElement: null, requiredRole: 'ejecutor' },
        4: { name: '4. Capacitación Comunitaria', amount: 25000, displayAmount: '$ 25.000', cid: 'N/A', status: 'PENDIENTE', isCompleted: false, actionElement: null, statusElement: null, cidDisplayElement: null, requiredRole: 'publico' },
    };

    /**
     * Formatea un número a moneda USD.
     */
    function formatUSD(number) {
        return new Intl.NumberFormat('en-US', { style: 'currency', currency: 'USD' }).format(number);
    }

    /**
     * Simula el proceso de inicio de sesión.
     */
    function login() {
        const roleSelect = document.getElementById('role-select');
        const usernameInput = document.getElementById('username');
        
        currentRole = roleSelect.value;
        const username = usernameInput.value;

        // Ocultar login y mostrar dashboard
        loginScreen.classList.add('hidden');
        dashboardScreen.classList.remove('hidden');

        // Inicializar la wallet y el dashboard
        initializeWallet(currentRole);
        updateDashboard(username, currentRole);
    }

    /**
     * Simula el proceso de cierre de sesión.
     */
    function logout() {
        dashboardScreen.classList.add('hidden');
        loginScreen.classList.remove('hidden');
        currentRole = 'publico'; 
        // Limpiar notificaciones
        notificationArea.classList.add('hidden');
        notificationArea.textContent = '';
    }

    /**
     * Inicializa y actualiza la información de la Wallet simulada.
     */
    function initializeWallet(role) {
        const walletData = actorWallets[role];

        if (role === 'publico') {
            walletAddressElement.textContent = 'Wallet Inactiva (Solo Vista)';
            walletBalanceElement.textContent = formatUSD(0);
            walletRoleTagElement.textContent = 'Solo Vista';
        } else {
            // Dirección corta para la visualización
            const shortAddress = walletData.address.substring(0, 10) + '...' + walletData.address.substring(walletData.address.length - 4);
            walletAddressElement.textContent = shortAddress;
            walletBalanceElement.textContent = formatUSD(walletData.balance);
            walletRoleTagElement.textContent = getRoleName(role);
        }
    }

    /**
     * Actualiza la interfaz del dashboard basándose en el rol actual y aplica permisos.
     */
    function updateDashboard(username, role) {
        welcomeUser.textContent = `Bienvenido(a), ${username} - Rol: ${getRoleName(role)}`;
        disbursedFundsElement.textContent = formatUSD(disbursedFunds);
        
        // Control de acciones y mensajes por rol
        for (let id in milestones) {
            const milestone = milestones[id];
            if (milestone.actionElement) {
                // Deshabilitar botones por defecto
                milestone.actionElement.disabled = true;

                // --- LÓGICA DE PERMISOS ---
                
                // Hito 2: EN REVISIÓN. Solo Validador puede Aprobar/Rechazar.
                if (id == 2 && milestone.status === 'EN REVISIÓN' && role === 'validador') {
                    milestone.actionElement.disabled = false;
                } 
                // Hito 3: PENDIENTE. Solo Ejecutor puede Subir Evidencias.
                else if (id == 3 && milestone.status === 'PENDIENTE' && role === 'ejecutor') {
                    milestone.actionElement.disabled = false;
                }
                // Hito 3: EN REVISIÓN. Solo Validador puede Aprobar/Rechazar. (Hito 3 aún no pasa a este estado)
                else if (id == 3 && milestone.status === 'EN REVISIÓN' && role === 'validador') {
                    milestone.actionElement.disabled = false;
                    milestone.actionElement.textContent = 'Validar'; // Cambia el texto del botón si el validador lo ve
                } 
                // Cualquier otro caso: El botón debe estar deshabilitado o tener un mensaje neutral.
                else if (milestone.status === 'VALIDADO') {
                     milestone.actionElement.textContent = 'Pagado';
                } else if (milestone.status === 'EN REVISIÓN') {
                    milestone.actionElement.textContent = 'En Validación';
                }
            }
        }

        // Actualizar mensaje de rol
        if (role === 'validador') {
            roleInfo.innerHTML = '<span class="font-bold">ROL VALIDADOR:</span> Tienes el permiso exclusivo para **APROBAR** hitos que están <span class="text-yellow-800">EN REVISIÓN</span>, liberando los fondos al Ejecutor. (Ej: Hito 2)';
        } else if (role === 'ejecutor') {
            roleInfo.innerHTML = '<span class="font-bold">ROL EJECUTOR:</span> Tienes el permiso exclusivo para **SUBIR EVIDENCIAS** de hitos <span class="text-gray-800">PENDIENTES</span>, poniéndolos <span class="text-yellow-800">EN REVISIÓN</span>. Los fondos se depositarán en tu Wallet simulada tras la validación.';
        } else if (role === 'financiador') {
            roleInfo.innerHTML = '<span class="font-bold">ROL FINANCIADOR:</span> Tienes visibilidad completa. No tienes permisos de acción directa, solo de monitoreo. Debes tener el saldo más alto en tu Wallet simulada.';
        } else { // publico
            roleInfo.innerHTML = '<span class="font-bold">ACCESO PÚBLICO:</span> Solo puedes visualizar el estado del proyecto y las transacciones validadas en Blockchain. No tienes permisos de acción.';
        }
    }

    /**
     * Devuelve el nombre amigable del rol.
     */
    function getRoleName(role) {
        switch (role) {
            case 'financiador': return 'Financiador';
            case 'ejecutor': return 'Ejecutor';
            case 'validador': return 'Validador Comunitario';
            default: return 'Público';
        }
    }

    /**
     * Abre la modal de detalle de hito, configurándola según el rol y el hito.
     */
    function openMilestoneModal(hitoId, requiredRole) {
        // --- CONTROL DE PERMISOS CLAVE ---
        if (currentRole !== requiredRole) {
            alertUser(`ACCESO DENEGADO: Solo el rol '${getRoleName(requiredRole)}' puede realizar esta acción. Tu rol actual es '${getRoleName(currentRole)}'.`, 'error');
            return;
        }

        currentMilestoneId = hitoId;
        const milestone = milestones[hitoId];

        // Control adicional para Validador (solo puede actuar si el estado es EN REVISIÓN)
        if (currentRole === 'validador' && milestone.status !== 'EN REVISIÓN') {
            alertUser(`ACCESO DENEGADO: El Hito ${hitoId} no está listo para validación. Estado actual: ${milestone.status}.`, 'error');
            return;
        }
        
        // Control adicional para Ejecutor (solo puede actuar si el estado es PENDIENTE)
        if (currentRole === 'ejecutor' && milestone.status !== 'PENDIENTE') {
            alertUser(`ACCESO DENEGADO: El Hito ${hitoId} ya fue subido o está pagado. Estado actual: ${milestone.status}.`, 'error');
            return;
        }


        // Rellenar información general
        document.getElementById('current-hito-name').textContent = milestone.name;
        document.getElementById('current-hito-amount').textContent = milestone.displayAmount;

        // Mostrar formulario específico
        document.getElementById('validador-form').classList.add('hidden');
        document.getElementById('ejecutor-form').classList.add('hidden');
        
        if (currentRole === 'validador') {
            document.getElementById('modal-title').textContent = 'Validar Hito ' + hitoId + ' (Liberar Fondos)';
            document.getElementById('validador-form').classList.remove('hidden');
            document.getElementById('validador-cid').textContent = milestone.cid + ' (Ver en IPFS)';
        } else if (currentRole === 'ejecutor') {
            document.getElementById('modal-title').textContent = 'Subir Evidencias Hito ' + hitoId;
            document.getElementById('ejecutor-form').classList.remove('hidden');
        }

        milestoneModal.classList.remove('hidden');
        milestoneModal.classList.add('flex');
        notificationArea.classList.add('hidden'); // Ocultar notificaciones al abrir modal
    }

    /**
     * Cierra la modal de detalle de hito.
     */
    function closeMilestoneModal() {
        milestoneModal.classList.add('hidden');
        milestoneModal.classList.remove('flex');
        currentMilestoneId = null;
    }

    /**
     * Simula la acción de APROBAR/RECHAZAR del Validador.
     */
    function performValidation(isApproved) {
        if (currentMilestoneId === 2 || currentMilestoneId === 3) {
            const milestone = milestones[currentMilestoneId];
            closeMilestoneModal();
            
            // Si el Ejecutor recibe el pago
            const amountToTransfer = milestone.amount;

            if (isApproved) {
                // 1. Lógica de Actualización de Wallet del Ejecutor (Receptor del Pago)
                actorWallets['ejecutor'].balance += amountToTransfer;
                disbursedFunds += amountToTransfer;
                
                // 2. Actualizar modelo de datos (simulado)
                milestone.status = 'VALIDADO';
                milestone.isCompleted = true;

                // 3. Actualizar interfaz
                milestone.statusElement.textContent = 'VALIDADO';
                milestone.statusElement.classList.remove('bg-yellow-100', 'text-yellow-800', 'bg-gray-100', 'text-gray-800');
                milestone.statusElement.classList.add('bg-green-100', 'text-green-800');
                
                milestone.actionElement.disabled = true;
                milestone.actionElement.textContent = 'Pagado (Contrato)';
                
                // Actualizar la wallet del actor logueado si es Ejecutor o Validador (solo para ver el saldo actualizado si es ejecutor)
                initializeWallet(currentRole);

                // Actualizar métrica de fondos desembolsados
                disbursedFundsElement.textContent = formatUSD(disbursedFunds);


                // 4. Registrar en el historial
                addTransactionToHistory(
                    `Hito ${currentMilestoneId}: ${milestone.name} APROBADO`,
                    'PaymentReleased',
                    `Monto Liberado: ${milestone.displayAmount} -> Wallet Ejecutor`,
                    'green-500'
                );

                alertUser(`Hito ${currentMilestoneId} Aprobado y Pagado! Contrato liberó ${milestone.displayAmount} a la Wallet del Ejecutor.`, 'success');

                // Si Hito 3 fue validado, el Hito 4 está listo para ser ejecutado (si su rol es ejecutor)
                if (currentMilestoneId === 3) {
                    milestones[4].status = 'PENDIENTE'; // Aunque ya estaba, lo confirmamos
                }

            } else {
                // Lógica de Rechazo (simulación)
                milestone.status = 'PENDIENTE';
                milestone.statusElement.textContent = 'RECHAZADO';
                milestone.statusElement.classList.remove('bg-yellow-100', 'text-yellow-800');
                milestone.statusElement.classList.add('bg-red-100', 'text-red-800');
                
                milestone.actionElement.textContent = 'Subir Evidencias';
                milestone.actionElement.disabled = (currentRole !== 'ejecutor'); // El ejecutor debe poder volver a subir

                // Registrar en el historial
                 addTransactionToHistory(
                    `Hito ${currentMilestoneId}: ${milestone.name} RECHAZADO`,
                    'MilestoneRejected',
                    `Evidencia revisada: ${milestone.cid}`,
                    'red-500'
                );

                alertUser(`Hito ${currentMilestoneId} Rechazado. Se requiere que el Ejecutor vuelva a subir las evidencias.`, 'error');
            }
            // Asegurarse de que el dashboard se actualice correctamente después de la acción
            updateDashboard(document.getElementById('username').value, currentRole);
        }
    }

    /**
     * Simula la acción de SUBIR EVIDENCIAS del Ejecutor.
     */
    function performExecutionSubmit() {
        if (currentMilestoneId === 3) {
            const milestone = milestones[currentMilestoneId];
            const newCid = document.getElementById('new-cid').value;
            closeMilestoneModal();

            // Actualizar modelo de datos (simulado)
            milestone.status = 'EN REVISIÓN';
            milestone.cid = newCid.substring(0, 7) + '...' + newCid.substring(newCid.length - 4); // Simular acortamiento
            document.getElementById('hito3-cid-display').textContent = milestone.cid; // Actualizar CID en la tabla

            // Actualizar interfaz
            milestone.statusElement.textContent = 'EN REVISIÓN';
            milestone.statusElement.classList.remove('bg-gray-100', 'text-gray-800', 'bg-red-100', 'text-red-800');
            milestone.statusElement.classList.add('bg-yellow-100', 'text-yellow-800');
            
            milestone.actionElement.disabled = true;
            milestone.actionElement.textContent = 'En Validación';

            // Registrar en el historial
            addTransactionToHistory(
                `Hito ${currentMilestoneId}: ${milestone.name} Evidencias Subidas`,
                'MilestoneSubmitted',
                `Evidencia CID: ${milestone.cid}`,
                'blue-500'
            );

            alertUser(`Evidencias subidas! Hito ${currentMilestoneId} ahora está en espera de la validación comunitaria.`, 'info');
            // Asegurarse de que el dashboard se actualice correctamente después de la acción
            updateDashboard(document.getElementById('username').value, currentRole);
        }
    }

    /**
     * Agrega una nueva transacción simulada al historial.
     */
    function addTransactionToHistory(title, eventName, detail, colorClass) {
        const date = new Date().toISOString().substring(0, 10);
        const txHash = '0x' + Math.random().toString(16).substring(2, 10).toUpperCase() + '...' + Math.random().toString(16).substring(2, 6).toUpperCase();

        const li = document.createElement('li');
        li.className = `p-3 bg-gray-50 rounded-lg border-l-4 border-${colorClass}`;
        li.innerHTML = `
            <p class="font-semibold text-gray-800">${title}</p>
            <p class="text-xs text-gray-500">Fecha: ${date} | Evento: ${eventName} | Tx Hash: <span class="text-blue-500">${txHash}</span></p>
            <p class="text-xs text-gray-700">${detail} | Actor: ${getRoleName(currentRole)}</p>
        `;
        // Agrega la nueva transacción al inicio de la lista
        transactionHistoryList.prepend(li);
    }

    /**
     * Muestra una notificación temporal en lugar de usar alert().
     */
    function alertUser(message, type = 'info') {
        let bgColor, textColor;
        if (type === 'success') {
            bgColor = 'bg-green-500';
            textColor = 'text-white';
        } else if (type === 'error') {
            bgColor = 'bg-red-500';
            textColor = 'text-white';
        } else { // info
            bgColor = 'bg-blue-500';
            textColor = 'text-white';
        }

        const notification = document.createElement('div');
        notification.textContent = message;
        notification.className = `fixed top-4 right-4 p-3 ${bgColor} ${textColor} rounded-lg shadow-xl z-50 transition-opacity duration-300 transform translate-y-0 opacity-100`;
        
        // Estilo de transición inicial
        notification.style.opacity = '0';
        document.body.appendChild(notification);
        
        // Aplicar fade-in
        setTimeout(() => {
            notification.style.transition = 'opacity 0.3s, transform 0.3s';
            notification.style.opacity = '1';
        }, 10);

        // Desaparecer después de 4 segundos
        setTimeout(() => {
            notification.style.opacity = '0';
            setTimeout(() => notification.remove(), 300);
        }, 4000);
    }

    // Inicializar el estado de los botones cuando la página carga
    window.onload = () => {
        // Asignar elementos DOM a los objetos del hito
        milestones[2].actionElement = document.getElementById('hito2-action');
        milestones[3].actionElement = document.getElementById('hito3-action');
        milestones[2].statusElement = document.getElementById('hito2-status');
        milestones[3].statusElement = document.getElementById('hito3-status');
        milestones[3].cidDisplayElement = document.getElementById('hito3-cid-display');

        // Asignar los handlers de la modal
        milestones[2].actionElement.onclick = () => openMilestoneModal(2, 'validador');
        milestones[3].actionElement.onclick = () => openMilestoneModal(3, 'ejecutor');
        
        // Inicializar el dashboard con el rol por defecto ('publico')
        updateDashboard(document.getElementById('username').value, currentRole);
    };

</script>

</body>
</html>
