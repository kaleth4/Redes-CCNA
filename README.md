###Redes
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Redes CCNA - Documentación y Labs</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
</head>
<body class="bg-slate-50 text-slate-800 font-sans">

    <header class="bg-blue-700 text-white py-12 shadow-lg">
        <div class="container mx-auto px-6 text-center">
            <h1 class="text-4xl md:text-5xl font-bold mb-4">🎓 Certificación CCNA 200-301</h1>
            <p class="text-xl text-blue-100">Topologías, Conceptos Fundamentales y Pentesting de Redes</p>
        </div>
    </header>

    <main class="container mx-auto px-6 py-10">
        
        <section class="grid md:grid-cols-2 gap-8 mb-16">
            <div class="bg-white p-8 rounded-xl shadow-md border-t-4 border-blue-500">
                <h2 class="text-2xl font-bold mb-4"><i class="fas fa-project-diagram mr-2"></i> Topologías de Red</h2>
                <ul class="space-y-3">
                    <li><strong>Estrella:</strong> Nodo central (Switch). Estándar en LAN.</li>
                    <li><strong>Malla:</strong> Alta redundancia, todos conectados con todos.</li>
                    <li><strong>Árbol:</strong> Estructura jerárquica escalable.</li>
                    <li><strong>Anillo & Bus:</strong> Modelos legacy y específicos.</li>
                </ul>
            </div>

            <div class="bg-white p-8 rounded-xl shadow-md border-t-4 border-green-500">
                <h2 class="text-2xl font-bold mb-4"><i class="fas fa-layer-group mr-2"></i> Modelos de Referencia</h2>
                <div class="flex justify-between gap-4 text-sm">
                    <div class="w-1/2">
                        <h3 class="font-bold border-b mb-2">Modelo OSI</h3>
                        <ol class="list-decimal list-inside">
                            <li>Física</li><li>Enlace</li><li>Red</li><li>Transporte</li><li>Sesión</li><li>Presentación</li><li>Aplicación</li>
                        </ol>
                    </div>
                    <div class="w-1/2">
                        <h3 class="font-bold border-b mb-2">Modelo TCP/IP</h3>
                        <ol class="list-decimal list-inside">
                            <li>Acceso a Red</li><li>Internet</li><li>Transporte</li><li>Aplicación</li>
                        </ol>
                    </div>
                </div>
            </div>
        </section>

        <section class="bg-slate-800 text-white p-8 rounded-xl shadow-2xl mb-16">
            <h2 class="text-3xl font-bold mb-6 text-blue-400"><i class="fas fa-terminal mr-2"></i> Laboratorio de Cisco: Router-on-a-Stick</h2>
            <div class="grid md:grid-cols-2 gap-8">
                <div>
                    <h3 class="text-xl font-semibold mb-3">Objetivos de Configuración</h3>
                    <p class="text-slate-300 mb-4">Resolución de problemas en VLAN 10 y 20, configuración de enlaces troncales 802.1Q.</p>
                    <div class="bg-slate-900 p-4 rounded font-mono text-sm text-green-400">
                        # Conf. Subinterfaz en R1<br>
                        interface g0/0.10<br>
                        encapsulation dot1Q 10<br>
                        ip address 192.168.10.1 255.255.255.0
                    </div>
                </div>
                <div class="border border-slate-700 p-4 rounded bg-slate-700/50">
                    <h3 class="text-xl font-semibold mb-3">Checklist del Lab</h3>
                    <ul class="space-y-2 text-slate-300">
                        <li><i class="fas fa-check-circle text-blue-400 mr-2"></i> Inicialización de S1 y S2</li>
                        <li><i class="fas fa-check-circle text-blue-400 mr-2"></i> Asignación de Puertos F0/6-12</li>
                        <li><i class="fas fa-check-circle text-blue-400 mr-2"></i> Verificación de Conectividad ICMP</li>
                    </ul>
                </div>
            </div>
        </section>

        <section class="mb-16">
            <h2 class="text-3xl font-bold text-center mb-10 underline decoration-red-500">🛡️ Redes en el Pentesting</h2>
            <div class="grid md:grid-cols-3 gap-6 text-center">
                <div class="p-6 bg-white rounded-lg shadow hover:shadow-xl transition">
                    <i class="fas fa-search text-4xl text-red-500 mb-4"></i>
                    <h3 class="font-bold text-xl mb-2">Nmap & Escaneo</h3>
                    <p class="text-sm text-gray-600">Descubrimiento de servicios y sigilo TCP.</p>
                </div>
                <div class="p-6 bg-white rounded-lg shadow hover:shadow-xl transition">
                    <i class="fas fa-user-secret text-4xl text-red-500 mb-4"></i>
                    <h3 class="font-bold text-xl mb-2">MITM Attacks</h3>
                    <p class="text-sm text-gray-600">ARP Spoofing e interceptación con Bettercap.</p>
                </div>
                <div class="p-6 bg-white rounded-lg shadow hover:shadow-xl transition">
                    <i class="fas fa-wifi text-4xl text-red-500 mb-4"></i>
                    <h3 class="font-bold text-xl mb-2">Wireless Hacking</h3>
                    <p class="text-sm text-gray-600">Captura de Handshakes y Evil Twin attacks.</p>
                </div>
            </div>
        </section>

    </main>

    <footer class="bg-slate-900 text-slate-400 py-8 text-center border-t border-slate-800">
        <p>Repositorio Redes-CCNA &copy; 2026 - Configurado para GitHub Pages</p>
    </footer>

</body>
</html>
