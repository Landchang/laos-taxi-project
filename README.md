<!DOCTYPE html>
<html lang="lo">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ທັນໃຈ ແທັກຊີ່ລາວ - ບໍລິການຂົນສົ່ງພາຍໃນ ແລະ ຕ່າງແຂວງ</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <!-- 
        *** IMPORTANT: Google Maps API Script ***
        You MUST replace 'YOUR_GOOGLE_MAPS_API_KEY' with your actual key 
        to enable the Autocomplete and Distance Matrix features. 
        Note: You must enable both 'Places API' and 'Distance Matrix API' in your Google Cloud Console.
        
        *** MOCK MODE: If the key below is not replaced, the system will enter mock mode. ***
    -->
    <script src="https://maps.googleapis.com/maps/api/js?key=YOUR_GOOGLE_MAPS_API_KEY&libraries=places&callback=initAutocomplete" async defer></script>
    <style>
        /* Custom Font for readability in Lao */
        @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+Lao:wght@100..900&display=swap');
        body {
            font-family: 'Noto Sans Lao', sans-serif;
            background-color: #f8f9fa;
        }
        .text-primary { color: #007bff; } /* Blue for primary accents */
        .bg-primary { background-color: #007bff; }
        .text-secondary { color: #495057; }
        .btn-primary {
            @apply bg-orange-500 hover:bg-orange-600 text-white font-bold py-3 px-6 rounded-lg shadow-lg transition duration-300 transform hover:scale-[1.02] flex items-center justify-center;
        }

        /* NEW: Custom CSS to hide scrollbar while allowing scrolling via buttons/touch */
        .custom-scrollbar::-webkit-scrollbar {
            display: none;
        }
        .custom-scrollbar {
            -ms-overflow-style: none;  /* IE and Edge */
            scrollbar-width: none;  /* Firefox */
        }
    </style>
</head>
<body class="antialiased">

    <!-- Header / Navigation Bar -->
    <header class="shadow-md bg-white sticky top-0 z-10">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4 flex justify-between items-center">
            <h1 class="text-2xl font-extrabold text-blue-700">ທັນໃຈ ແທັກຊີ່ລາວ</h1>
            <a href="#contact" class="hidden md:block btn-primary py-2 px-4 text-sm">
                <i data-lucide="phone" class="w-4 h-4 mr-2"></i> ໂທຈອງດ່ວນ
            </a>
            <button class="md:hidden p-2 text-blue-700 rounded-lg hover:bg-gray-100" onclick="document.getElementById('mobile-menu').classList.toggle('hidden')">
                <i data-lucide="menu" class="w-6 h-6"></i>
            </button>
        </div>
        <!-- Mobile Menu -->
        <div id="mobile-menu" class="hidden md:hidden bg-white px-4 pb-2">
            <a href="#services" class="block py-2 text-blue-700 font-medium hover:bg-gray-100 rounded-md">ບໍລິການ</a>
            <a href="#booking" class="block py-2 text-blue-700 font-medium hover:bg-gray-100 rounded-md">ຈອງລົດ</a>
            <a href="#contact" class="block py-2 text-blue-700 font-medium hover:bg-gray-100 rounded-md">ຕິດຕໍ່</a>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="relative bg-cover bg-center bg-gray-900" 
             style="background-image: url('https://placehold.co/1200x600/007bff/ffffff?text=Laos+Taxi+Service');">
        <div class="absolute inset-0 bg-black opacity-60"></div>
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-20 md:py-32 relative text-white text-center">
            <h2 class="text-4xl sm:text-5xl lg:text-6xl font-extrabold mb-4 leading-tight">
                ບໍລິການຂົນສົ່ງປອດໄພ ຈາກວຽງຈັນ ຫາ ທຸກແຂວງ
            </h2>
            <p class="text-xl sm:text-2xl mb-8">
                ລົດໃໝ່, ຄົນຂັບເຊື່ອຖືໄດ້, ລາຄາຊັດເຈນ 24 ຊົ່ວໂມງ.
            </p>
            <a href="#booking" class="btn-primary inline-flex text-xl">
                <i data-lucide="car" class="w-6 h-6 mr-3"></i> ກົດຈອງດ່ວນ / ຂໍລາຄາ
            </a>
        </div>
    </section>

    <!-- Services Section -->
    <section id="services" class="py-16 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <h3 class="text-3xl font-bold text-center text-blue-700 mb-12">ບໍລິການຫຼັກຂອງພວກເຮົາ</h3>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <!-- Service 1: Local -->
                <div class="bg-gray-50 p-6 rounded-xl shadow-lg hover:shadow-xl transition duration-300">
                    <div class="bg-blue-100 text-blue-700 rounded-full w-12 h-12 flex items-center justify-center mb-4">
                        <i data-lucide="map-pin" class="w-6 h-6"></i>
                    </div>
                    <h4 class="text-xl font-bold mb-3 text-blue-700">ແທັກຊີ່ພາຍໃນເມືອງ</h4>
                    <p class="text-secondary text-base">ຮັບ-ສົ່ງດ່ວນໃນຕົວເມືອງວຽງຈັນ, ຫຼວງພະບາງ, ແລະ ເມືອງໃຫຍ່ອື່ນໆ. ຮັບປະກັນຄວາມວ່ອງໄວ.</p>
                </div>
                <!-- Service 2: Airport -->
                <div class="bg-gray-50 p-6 rounded-xl shadow-lg hover:shadow-xl transition duration-300">
                    <div class="bg-blue-100 text-blue-700 rounded-full w-12 h-12 flex items-center justify-center mb-4">
                        <i data-lucide="plane" class="w-6 h-6"></i>
                    </div>
                    <h4 class="text-xl font-bold mb-3 text-blue-700">ບໍລິການໄປສະໜາມບິນ</h4>
                    <p class="text-secondary text-base">ລາຄາເໝົາພິເສດສຳລັບສະໜາມບິນສາກົນວັດໄຕ. ບໍ່ມີຄ່າໃຊ້ຈ່າຍເພີ່ມເຕີມໃນຕອນກາງຄືນ.</p>
                </div>
                <!-- Service 3: Inter-Province -->
                <div class="bg-gray-50 p-6 rounded-xl shadow-lg hover:shadow-xl transition duration-300">
                    <div class="bg-blue-100 text-blue-700 rounded-full w-12 h-12 flex items-center justify-center mb-4">
                        <i data-lucide="road" class="w-6 h-6"></i>
                    </div>
                    <h4 class="text-xl font-bold mb-3 text-blue-700">ຂົນສົ່ງຕ່າງແຂວງ</h4>
                    <p class="text-secondary text-base">ເດີນທາງດ້ວຍລົດສ່ວນຕົວໄປທຸກແຂວງ. ປອດໄພ ແລະ ສະດວກສະບາຍສຳລັບທຸລະກິດ ແລະ ການທ່ອງທ່ຽວ.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Booking / Fare Inquiry Form Section -->
    <section id="booking" class="py-16 bg-blue-700">
        <div class="max-w-3xl mx-auto px-4 sm:px-6 lg:px-8">
            <h3 class="text-3xl font-bold text-center text-white mb-8">ສົ່ງຄຳສັ່ງຈອງ ແລະ ຂໍລາຄາ</h3>
            <p class="text-center text-blue-100 mb-8">
                ກະລຸນາປ້ອນຂໍ້ມູນການເດີນທາງ (ໃຊ້ Google Maps ໄດ້). ລະບົບຈະຄິດໄລ່ລາຄາໂດຍປະມານໃຫ້ທ່ານທັນທີ.
            </p>

            <form id="booking-form" class="bg-white p-6 md:p-10 rounded-xl shadow-2xl">
                <!-- Origin and Destination Inputs (with Autocomplete) -->
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-6">
                    <div>
                        <label for="origin" class="block text-sm font-medium text-gray-700 mb-1">ຕົ້ນທາງ (Origin) - <span class="text-xs text-orange-500">ເລືອກຈາກແຜນທີ່</span></label>
                        <input type="text" id="origin" name="origin" required 
                               class="w-full border border-gray-300 p-3 rounded-lg focus:ring-blue-500 focus:border-blue-500" placeholder="ຕົວຢ່າງ: ສະໜາມບິນວັດໄຕ">
                    </div>
                    <div>
                        <label for="destination" class="block text-sm font-medium text-gray-700 mb-1">ປາຍທາງ (Destination) - <span class="text-xs text-orange-500">ເລືອກຈາກແຜນທີ່</span></label>
                        <input type="text" id="destination" name="destination" required 
                               class="w-full border border-gray-300 p-3 rounded-lg focus:ring-blue-500 focus:border-blue-500" placeholder="ຕົວຢ່າງ: ວັງວຽງ ຫຼື ໂຮງແຮມຂອງທ່ານ">
                    </div>
                </div>

                <!-- Car Type Selector (Triggers Recalculation) -->
                <div class="mb-6">
                    <label for="car_type" class="block text-sm font-medium text-gray-700 mb-1">ປະເພດລົດທີ່ຕ້ອງການ</label>
                    <select id="car_type" name="car_type" class="w-full border border-gray-300 p-3 rounded-lg focus:ring-blue-500 focus:border-blue-500">
                        <option value="ລົດເກັງ (1-3 ທ່ານ)">ລົດເກັງ (1-3 ທ່ານ)</option>
                        <option value="ລົດ SUV (1-4 ທ່ານ + ກະເປົາ)">ລົດ SUV (1-4 ທ່ານ + ກະເປົາ)</option>
                        <option value="ລົດຕູ້/ລົດແວນ (5-15 ທ່ານ)">ລົດຕູ້/ລົດແວນ (5-15 ທ່ານ)</option>
                    </select>
                </div>

                <!-- Calculation Results Display -->
                <div id="fare-results" class="bg-blue-50/50 p-4 rounded-lg border border-blue-200 mb-6 min-h-[80px]">
                    <p class="text-center text-gray-500 py-2">
                        ກະລຸນາເລືອກ **ຕົ້ນທາງ** ແລະ **ປາຍທາງ** ເພື່ອຄິດໄລ່ລາຄາ.
                    </p>
                </div>

                <!-- Hidden inputs to store calculated data for WhatsApp -->
                <input type="hidden" id="calculated-distance" name="calculated_distance" value="">
                <input type="hidden" id="calculated-fare" name="calculated_fare" value="0">


                <!-- Date, Time, and Phone Inputs -->
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-6">
                    <div>
                        <label for="date" class="block text-sm font-medium text-gray-700 mb-1">ວັນທີເດີນທາງ</label>
                        <input type="date" id="date" name="date" required 
                               class="w-full border border-gray-300 p-3 rounded-lg focus:ring-blue-500 focus:border-blue-500">
                    </div>
                    <div>
                        <label for="time" class="block text-sm font-medium text-gray-700 mb-1">ເວລາເດີນທາງ</label>
                        <input type="time" id="time" name="time" required 
                               class="w-full border border-gray-300 p-3 rounded-lg focus:ring-blue-500 focus:border-blue-500">
                    </div>
                </div>

                <div class="mb-8">
                    <label for="phone" class="block text-sm font-medium text-gray-700 mb-1">ເບີໂທລະສັບຕິດຕໍ່ (ສຳຄັນ)</label>
                    <input type="tel" id="phone" name="phone" required 
                           class="w-full border border-gray-300 p-3 rounded-lg focus:ring-blue-500 focus:border-blue-500" placeholder="ປ້ອນເບີ 020 XXXXXXXX">
                </div>
                
                <button type="submit" class="btn-primary w-full text-lg bg-green-500 hover:bg-green-600">
                    <i data-lucide="whatsapp" class="w-5 h-5 mr-3"></i> ສົ່ງຂໍ້ຄວາມຈອງຜ່ານ WhatsApp
                </button>
            </form>
        </div>
    </section>
    
    <!-- Service Area Map (Simple Embed) -->
    <section id="map" class="py-16 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <h3 class="text-3xl font-bold text-center text-blue-700 mb-8">ພື້ນທີ່ບໍລິການຫຼັກ</h3>
            <div class="rounded-xl overflow-hidden shadow-2xl">
                <!-- Replace 'Vientiane' with your specific city or coordinates if you have a Google Maps API Key -->
                <iframe 
                    width="100%" 
                    height="450" 
                    frameborder="0" 
                    style="border:0" 
                    src="https://www.google.com/maps/embed/v1/place?q=Vientiane,Laos&zoom=8&key=YOUR_GOOGLE_MAPS_API_KEY" 
                    allowfullscreen>
                </iframe>
            </div>
            <p class="text-center text-gray-600 mt-4 text-sm">ແຜນທີ່ສະແດງພື້ນທີ່ບໍລິການທົ່ວປະເທດລາວ. ທ່ານສາມາດຈອງລົດໄປຕ່າງແຂວງໄດ້.</p>
        </div>
    </section>

    <!-- UPDATED: Video Display Section (Operational/Safety Feature) - Now a Carousel Slider -->
    <section id="video-display" class="py-16 bg-red-50">
        <div class="max-w-3xl mx-auto px-4 sm:px-6 lg:px-8 p-6 rounded-xl shadow-xl border-t-4 border-red-500">
            <h3 class="text-2xl font-bold text-center text-red-700 mb-4">
                <i data-lucide="video" class="w-6 h-6 inline mr-2 text-red-600"></i> ວິດີໂອຈາກກ້ອງໃນຫ້ອງໂດຍສານ (Dashcam Clips)
            </h3>
            <p class="text-center text-gray-600 mb-6 text-sm md:text-base">
                (ໃຊ້ສຳລັບການກວດສອບຄວາມປອດໄພ ແລະ ການຝຶກອົບຮົມຄົນຂັບ. ສະໄລເບິ່ງໄດ້ 4 ຄລິບ.)
            </p>

            <div class="bg-white p-4 md:p-6 rounded-lg border border-red-200 relative">
                
                <!-- Carousel Controls -->
                <div class="flex justify-between absolute top-1/2 left-0 right-0 transform -translate-y-1/2 z-10 px-2 md:px-6">
                    <button id="prev-video" class="p-2 bg-white/50 text-red-600 rounded-full hover:bg-white transition shadow-lg" aria-label="Previous Video">
                        <i data-lucide="chevron-left" class="w-6 h-6"></i>
                    </button>
                    <button id="next-video" class="p-2 bg-white/50 text-red-600 rounded-full hover:bg-white transition shadow-lg" aria-label="Next Video">
                        <i data-lucide="chevron-right" class="w-6 h-6"></i>
                    </button>
                </div>

                <!-- Video Carousel Container -->
                <!-- Use w-full for flex-none item to ensure only one video is visible at a time for easy sliding -->
                <div id="video-carousel" class="flex overflow-x-scroll snap-x snap-mandatory space-x-4 custom-scrollbar">
                    
                    <!-- Video Clip 1 -->
                    <div class="flex-none w-full snap-center bg-gray-100 rounded-lg shadow-md overflow-hidden aspect-video">
                        <video controls class="w-full h-full object-cover" poster="https://placehold.co/600x337/8B0000/ffffff?text=Clip+1+Laos+Taxi">
                            <!-- MUST REPLACE source URLs with actual MP4 links -->
                            <source src="mock_dashcam_footage_1.mp4" type="video/mp4">
                            <p class="text-center p-4 text-red-500">ຄລິບທີ 1: ບໍ່ຮອງຮັບ</p>
                        </video>
                    </div>

                    <!-- Video Clip 2 -->
                    <div class="flex-none w-full snap-center bg-gray-100 rounded-lg shadow-md overflow-hidden aspect-video">
                        <video controls class="w-full h-full object-cover" poster="https://placehold.co/600x337/8B0000/ffffff?text=Clip+2+Laos+Taxi">
                            <source src="mock_dashcam_footage_2.mp4" type="video/mp4">
                            <p class="text-center p-4 text-red-500">ຄລິບທີ 2: ບໍ່ຮອງຮັບ</p>
                        </video>
                    </div>

                    <!-- Video Clip 3 -->
                    <div class="flex-none w-full snap-center bg-gray-100 rounded-lg shadow-md overflow-hidden aspect-video">
                        <video controls class="w-full h-full object-cover" poster="https://placehold.co/600x337/8B0000/ffffff?text=Clip+3+Laos+Taxi">
                            <source src="mock_dashcam_footage_3.mp4" type="video/mp4">
                            <p class="text-center p-4 text-red-500">ຄລິບທີ 3: ບໍ່ຮອງຮັບ</p>
                        </video>
                    </div>

                    <!-- Video Clip 4 -->
                    <div class="flex-none w-full snap-center bg-gray-100 rounded-lg shadow-md overflow-hidden aspect-video">
                        <video controls class="w-full h-full object-cover" poster="https://placehold.co/600x337/8B0000/ffffff?text=Clip+4+Laos+Taxi">
                            <source src="mock_dashcam_footage_4.mp4" type="video/mp4">
                            <p class="text-center p-4 text-red-500">ຄລິບທີ 4: ບໍ່ຮອງຮັບ</p>
                        </video>
                    </div>

                </div>
                <!-- End Video Carousel Container -->
                
                <div class="mt-4 text-sm text-gray-500">
                    <p>
                        <span class="font-semibold text-red-600">ໝາຍເຫດ:</span> 
                        ເພື່ອໃຫ້ຄລິບວິດີໂອຫຼິ້ນໄດ້ແທ້, ທ່ານຕ້ອງປ່ຽນ `mock_dashcam_footage_X.mp4` ໃນ Code ໃຫ້ເປັນລິ້ງວິດີໂອ MP4 ຕົວຈິງຂອງທ່ານ (ເຊັ່ນ: ທີ່ເກັບໄວ້ໃນ server).
                    </p>
                </div>
            </div>
        </div>
    </section>
    <!-- END UPDATED SECTION -->

    <!-- Contact Info Footer -->
    <footer id="contact" class="bg-gray-800 text-white py-12">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 grid grid-cols-1 md:grid-cols-3 gap-8 text-center md:text-left">
            <!-- Col 1: Logo/Slogan -->
            <div>
                <h4 class="text-2xl font-extrabold text-orange-500 mb-3">ທັນໃຈ ແທັກຊີ່ລາວ</h4>
                <p class="text-gray-400">ບໍລິການຂົນສົ່ງທີ່ທ່ານໄວ້ໃຈໄດ້ຕະຫຼອດ 24 ຊົ່ວໂມງ.</p>
            </div>
            
            <!-- Col 2: Quick Links -->
            <div>
                <h4 class="text-xl font-bold mb-4">ລິ້ງທີ່ສຳຄັນ</h4>
                <ul class="space-y-2">
                    <li><a href="#services" class="text-gray-400 hover:text-orange-500 transition duration-200">ປະເພດບໍລິການ</a></li>
                    <li><a href="#booking" class="text-gray-400 hover:text-orange-500 transition duration-200">ຂໍລາຄາ/ຈອງລົດ</a></li>
                    <li><a href="#" class="text-gray-400 hover:text-orange-500 transition duration-200">ກ່ຽວກັບພວກເຮົາ</a></li>
                </ul>
            </div>

            <!-- Col 3: Contact Details -->
            <div>
                <h4 class="text-xl font-bold mb-4">ຕິດຕໍ່ພວກເຮົາ</h4>
                <p class="flex items-center justify-center md:justify-start mb-2"><i data-lucide="phone" class="w-4 h-4 mr-2 text-orange-500"></i> **ໂທສາຍດ່ວນ (24/7): (020) 123 4567**</p>
                <p class="flex items-center justify-center md:justify-start mb-2"><i data-lucide="mail" class="w-4 h-4 mr-2 text-orange-500"></i> info@thanhjaitaxi.com</p>
                <p class="flex items-center justify-center md:justify-start"><i data-lucide="map-pin" class="w-4 h-4 mr-2 text-orange-500"></i> ນະຄອນຫຼວງວຽງຈັນ, ສ.ປ.ປ. ລາວ</p>
            </div>
        </div>
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 mt-8 pt-4 border-t border-gray-700 text-center text-gray-500 text-sm">
            &copy; 2025 Thanhjai Taxi Laos. ສະຫງວນລິຂະສິດ.
        </div>
    </footer>

    <!-- JavaScript for Form Handling, Icon Rendering, and Google Autocomplete/Distance Calculation -->
    <script>
        // Initialize Lucide icons
        lucide.createIcons();

        let mapService; // Google Distance Matrix Service instance
        
        // Check if the placeholder key is still in the script tag's src
        const isMockMode = document.querySelector('script[src*="YOUR_GOOGLE_MAPS_API_KEY"]') !== null;
        
        // ** CONSTANTS AND MOCK DATA **
        
        // Default location for the driver when calculating ETA to the customer (Real Mode)
        const DEFAULT_DRIVER_LOCATION = "Wattay International Airport, Vientiane, Laos"; 

        // Mock data for the main trip (Origin to Destination)
        const MOCK_DISTANCE_KM = 85.0; 
        const MOCK_DURATION_TEXT = "1 ຊົ່ວໂມງ 45 ນາທີ";

        // Mock data for the Driver ETA (Driver to Origin)
        const MOCK_DRIVER_ETA_MINUTES = 12; 
        const MOCK_DRIVER_ETA_TEXT = `${MOCK_DRIVER_ETA_MINUTES} ນາທີ`;

        /**
         * Simple hypothetical fare calculation model based on distance and car type.
         */
        function getFareModel(distanceKm, carType) {
            // Hypothetical Lao Kip (LAK) fare structure
            const LAK_PER_KM = 10000;  // 10,000 LAK per kilometer (ລາຄາຕໍ່ກິໂລ)
            const BASE_FARE = 30000;  // 30,000 LAK base fee (ຄ່າບໍລິການພື້ນຖານ)

            let multiplier = 1;

            switch (carType) {
                case 'ລົດເກັງ (1-3 ທ່ານ)':
                    multiplier = 1.0;
                    break;
                case 'ລົດ SUV (1-4 ທ່ານ + ກະເປົາ)':
                    multiplier = 1.2; // 20% higher for SUV
                    break;
                case 'ລົດຕູ້/ລົດແວນ (5-15 ທ່ານ)':
                    multiplier = 1.5; // 50% higher for Van
                    break;
            }

            const estimatedFare = (BASE_FARE + (distanceKm * LAK_PER_KM)) * multiplier;
            // Round to the nearest 1,000 LAK for clean display
            return Math.round(estimatedFare / 1000) * 1000; 
        }

        /**
         * Formats a number into LAK currency string.
         */
        function formatLAK(amount) {
            if (isNaN(amount) || amount <= 0) return '---';
            // Format number with comma as thousand separator, and append LAK symbol
            return amount.toLocaleString('en-US') + ' LAK';
        }
        
        // --- MOCK MODE FUNCTIONS ---

        /**
         * Simulates distance calculation and displays mock data.
         */
        function calculateMockRoute() {
            const carType = document.getElementById('car_type').value;
            const resultsDiv = document.getElementById('fare-results');
            
            const origin = document.getElementById('origin').value;
            const destination = document.getElementById('destination').value;

            // Only calculate if both inputs have some value (for user interaction simulation)
            if (!origin || !destination) {
                 resultsDiv.innerHTML = `<p class="text-center text-orange-500 py-2 font-bold">⚠️ ໂໝດຈຳລອງລາຄາ ເປີດໃຊ້ງານແລ້ວ. ປ້ອນຂໍ້ມູນໃດກໍໄດ້ເພື່ອເບິ່ງຜົນ.</p>`;
                 return;
            }

            const estimatedFare = getFareModel(MOCK_DISTANCE_KM, carType);

            // Store mock values in hidden inputs for use in WhatsApp message
            document.getElementById('calculated-distance').value = `${MOCK_DISTANCE_KM.toFixed(1)} km`;
            document.getElementById('calculated-fare').value = estimatedFare;

            // Display results in the UI with a MOCK MODE warning
            resultsDiv.innerHTML = `
                <div class="space-y-3">
                    <div class="flex justify-between items-center text-lg font-bold text-gray-700 border-b pb-2 text-orange-600">
                        <span><i data-lucide="alert-triangle" class="w-5 h-5 inline mr-2 text-orange-600"></i> ໂໝດຈຳລອງ: ລາຄາປະມານ!</span>
                        <span class="text-green-600 text-2xl">${formatLAK(estimatedFare)}</span>
                    </div>
                    <!-- NEW: Driver ETA in Mock Mode -->
                    <div class="flex justify-between text-base font-semibold text-blue-700 pt-2 border-t border-dashed">
                        <span><i data-lucide="map-pin" class="w-4 h-4 inline mr-1"></i> ລົດຮອດຈຸດຮັບລູກຄ້າປະມານ</span>
                        <span>${MOCK_DRIVER_ETA_TEXT}</span> 
                    </div>
                    <!-- END NEW -->
                    <div class="flex justify-between text-sm text-gray-500">
                        <span><i data-lucide="route" class="w-4 h-4 inline mr-1"></i> ໄລຍະທາງເດີນທາງ</span>
                        <span>${MOCK_DISTANCE_KM.toFixed(1)} km</span>
                    </div>
                    <div class="flex justify-between text-sm text-gray-500">
                        <span><i data-lucide="clock" class="w-4 h-4 inline mr-1"></i> ເວລາເດີນທາງ (ເຖິງປາຍທາງ)</span>
                        <span>${MOCK_DURATION_TEXT}</span>
                    </div>
                    <p class="text-xs text-red-500 mt-2">
                        *ເພື່ອໃຊ້ການຄຳນວນຈິງ, ກະລຸນາປ່ຽນ 'YOUR_GOOGLE_MAPS_API_KEY' ໃຫ້ເປັນລະຫັດຂອງທ່ານ.
                    </p>
                </div>
            `;
            lucide.createIcons();
        }

        /**
         * Initializes the UI for Mock Mode.
         */
        function initMockMode() {
            console.warn("MOCK MODE ACTIVE: Google Maps API key placeholder detected or API failed to load. Using sample data for calculation.");

            const originInput = document.getElementById('origin');
            const destinationInput = document.getElementById('destination');
            const carTypeSelect = document.getElementById('car_type');
            
            // In mock mode, attach event listeners to trigger mock calculation on change
            originInput.addEventListener('input', calculateMockRoute);
            destinationInput.addEventListener('input', calculateMockRoute);
            carTypeSelect.addEventListener('change', calculateMockRoute);

            // Set initial instruction for mock mode
            const resultsDiv = document.getElementById('fare-results');
            resultsDiv.innerHTML = `<p class="text-center text-orange-500 py-2 font-bold">⚠️ ໂໝດຈຳລອງລາຄາ ເປີດໃຊ້ງານແລ້ວ. ປ້ອນຂໍ້ມູນໃດກໍໄດ້ເພື່ອເບິ່ງຜົນ.</p>`;
            
            // Run initial calculation with mock data
            if (originInput.value && destinationInput.value) {
                calculateMockRoute();
            }
        }

        // --- REAL MODE FUNCTIONS ---
        
        // This function is called automatically when the Google Maps script loads successfully.
        function initAutocomplete() {
            if (typeof google === 'undefined' || typeof google.maps === 'undefined' || typeof google.maps.places === 'undefined' || isMockMode) {
                initMockMode();
                return;
            }

            mapService = new google.maps.DistanceMatrixService();

            const originInput = document.getElementById('origin');
            const destinationInput = document.getElementById('destination');
            const carTypeSelect = document.getElementById('car_type');
            
            const options = {
                fields: ["formatted_address"],
                types: ['geocode', 'establishment'], 
            };

            const originAutocomplete = new google.maps.places.Autocomplete(originInput, options);
            const destinationAutocomplete = new google.maps.places.Autocomplete(destinationInput, options);
            
            originAutocomplete.addListener('place_changed', calculateRoute);
            destinationAutocomplete.addListener('place_changed', calculateRoute);
            carTypeSelect.addEventListener('change', calculateRoute);
            
            originInput.addEventListener('blur', calculateRoute);
            destinationInput.addEventListener('blur', calculateRoute);
            
            console.log("REAL MODE ACTIVE: Google Maps Autocomplete initialized.");
        }


        /**
         * Calls Google Distance Matrix API twice: 1) Driver ETA, 2) Main Route Fare.
         */
        function calculateRoute() {
            if (typeof google === 'undefined' || typeof mapService === 'undefined' || isMockMode) {
                return calculateMockRoute();
            }

            const origin = document.getElementById('origin').value;
            const destination = document.getElementById('destination').value;
            const carType = document.getElementById('car_type').value;
            const resultsDiv = document.getElementById('fare-results');
            
            resultsDiv.innerHTML = `<p class="text-center text-gray-500 py-4"><i data-lucide="loader" class="w-5 h-5 inline animate-spin mr-2"></i> ກຳລັງຄິດໄລ່ລາຄາ...</p>`;
            lucide.createIcons();

            if (!origin || !destination) {
                resultsDiv.innerHTML = `<p class="text-center text-gray-400 py-4">ກະລຸນາເລືອກຕົ້ນທາງ ແລະ ປາຍທາງທີ່ຖືກຕ້ອງ.</p>`;
                document.getElementById('calculated-distance').value = '';
                document.getElementById('calculated-fare').value = 0;
                return;
            }
            
            let driverEtaText = "ບໍ່ສາມາດຄຳນວນໄດ້"; // Default placeholder if ETA calculation fails

            // 1. Calculate Driver ETA (Driver Depot -> Origin)
            mapService.getDistanceMatrix({
                origins: [DEFAULT_DRIVER_LOCATION],
                destinations: [origin],
                travelMode: google.maps.TravelMode.DRIVING,
                unitSystem: google.maps.UnitSystem.METRIC,
            }, (driverResponse, driverStatus) => {
                
                if (driverStatus === 'OK' && driverResponse.rows[0].elements[0].status === 'OK') {
                    const driverElement = driverResponse.rows[0].elements[0];
                    driverEtaText = driverElement.duration.text;
                } else {
                    console.error('Error calculating Driver ETA:', driverStatus, driverResponse.rows[0].elements[0].status);
                    // Use the default "ບໍ່ສາມາດຄຳນວນໄດ້"
                }
                
                // 2. Calculate Main Route (Origin -> Destination)
                mapService.getDistanceMatrix({
                    origins: [origin],
                    destinations: [destination],
                    travelMode: google.maps.TravelMode.DRIVING,
                    unitSystem: google.maps.UnitSystem.METRIC,
                }, (response, status) => {
                    if (status !== 'OK') {
                        resultsDiv.innerHTML = `<p class="text-center text-red-500 py-4">ຂໍອະໄພ, ບໍ່ສາມາດຊອກຫາເສັ້ນທາງໄດ້: ${status}. ກະລຸນາຕິດຕໍ່ບໍລິສັດໂດຍກົງ.</p>`;
                        document.getElementById('calculated-distance').value = '';
                        document.getElementById('calculated-fare').value = 0;
                        return;
                    }

                    const element = response.rows[0].elements[0];
                    
                    if (element.status === 'OK') {
                        const distanceMeters = element.distance.value;
                        const distanceText = element.distance.text;
                        const durationText = element.duration.text;
                        
                        const distanceKm = distanceMeters / 1000;
                        const estimatedFare = getFareModel(distanceKm, carType);

                        document.getElementById('calculated-distance').value = distanceText;
                        document.getElementById('calculated-fare').value = estimatedFare;

                        // Display results in the UI, now including the Driver ETA
                        resultsDiv.innerHTML = `
                            <div class="space-y-3">
                                <div class="flex justify-between items-center text-lg font-semibold text-gray-700 border-b pb-2">
                                    <span><i data-lucide="calculator" class="w-5 h-5 inline mr-2 text-blue-500"></i> ລາຄາຄຳນວນ (ປະມານ)</span>
                                    <span class="text-green-600 text-2xl">${formatLAK(estimatedFare)}</span>
                                </div>
                                <!-- NEW: Driver ETA -->
                                <div class="flex justify-between text-base font-semibold text-blue-700 pt-2 border-t border-dashed">
                                    <span><i data-lucide="map-pin" class="w-4 h-4 inline mr-1"></i> ລົດຮອດຈຸດຮັບລູກຄ້າປະມານ</span>
                                    <span>${driverEtaText}</span> 
                                </div>
                                <!-- END NEW -->
                                <div class="flex justify-between text-sm text-gray-500">
                                    <span><i data-lucide="route" class="w-4 h-4 inline mr-1"></i> ໄລຍະທາງເດີນທາງ</span>
                                    <span>${distanceText}</span>
                                </div>
                                <div class="flex justify-between text-sm text-gray-500">
                                    <span><i data-lucide="clock" class="w-4 h-4 inline mr-1"></i> ເວລາເດີນທາງ (ເຖິງປາຍທາງ)</span>
                                    <span>${durationText}</span>
                                </div>
                            </div>
                        `;
                    } else {
                        resultsDiv.innerHTML = `<p class="text-center text-orange-500 py-4">ບໍ່ສາມາດຄິດໄລ່ເສັ້ນທາງທີ່ຖືກຕ້ອງໄດ້. (${element.status})</p>`;
                        document.getElementById('calculated-distance').value = '';
                        document.getElementById('calculated-fare').value = 0;
                    }
                    lucide.createIcons();
                });
            });
        }
        // ** END Autocomplete and Distance Calculation **
        
        // Manual initialization for mock mode if placeholder key is detected immediately
        if (isMockMode) {
            document.addEventListener('DOMContentLoaded', initMockMode);
        }


        // Simple form submission handler (WhatsApp redirection)
        document.getElementById('booking-form').addEventListener('submit', function(event) {
            event.preventDefault();
            
            // 1. Gather form data into an object
            const formData = new FormData(this);
            const data = {};
            formData.forEach((value, key) => {
                data[key] = value;
            });
            
            // Get calculated values from hidden inputs
            const calculatedDistance = document.getElementById('calculated-distance').value;
            const calculatedFare = document.getElementById('calculated-fare').value;

            const fareDisplay = calculatedFare > 0 ? formatLAK(parseFloat(calculatedFare)) : 'ຍັງບໍ່ໄດ້ຄິດໄລ່/ກະລຸນາຢືນຢັນ';
            const distanceDisplay = calculatedDistance || 'ຍັງບໍ່ໄດ້ຄິດໄລ່';

            
            // ** IMPORTANT: Replace '+8562098767276' with your actual WhatsApp phone number (Laos code +85620) **
            const whatsappNumber = '+8562098767276'; 
            
            // 2. Construct the pre-filled message in Lao, including calculated details
            const message = `
*ຄຳສັ່ງຈອງລົດແທັກຊີ່ ທັນໃຈ ແທັກຊີ່ລາວ*

ຂ້າພະເຈົ້າຕ້ອງການຈອງລົດແທັກຊີ່. ກະລຸນາຢືນຢັນລາຄາ ແລະ ການຈອງ:
ຕົ້ນທາງ: ${data.origin}
ປາຍທາງ: ${data.destination}
ວັນທີ: ${data.date}
ເວລາ: ${data.time}
ເບີໂທຕິດຕໍ່: ${data.phone}
ປະເພດລົດ: ${data.car_type}

---
*ຂໍ້ມູນການຄິດໄລ່ໂດຍປະມານ (ກ່ອນຢືນຢັນ):*
**ລົດຮອດຈຸດຮັບລູກຄ້າ: (ຂໍ້ມູນຈະຄິດໄລ່ເມື່ອໃຊ້ API Key ຕົວຈິງ) **
ໄລຍະທາງເດີນທາງ: ${distanceDisplay}
ລາຄາຄຳນວນ (ປະມານ): ${fareDisplay}
            `.trim(); // trim to remove leading/trailing whitespace

            // 3. Encode the message for the URL and create the WhatsApp link
            const encodedMessage = encodeURIComponent(message);
            const whatsappLink = `https://wa.me/${whatsappNumber}?text=${encodedMessage}`;

            // 4. Redirect the user to WhatsApp
            window.open(whatsappLink, '_blank');
        });
        
        // ** NEW: JavaScript for Video Carousel Sliding **
        document.addEventListener('DOMContentLoaded', () => {
            const carousel = document.getElementById('video-carousel');
            const prevButton = document.getElementById('prev-video');
            const nextButton = document.getElementById('next-video');

            if (carousel && prevButton && nextButton) {
                // Function to calculate the scroll amount (the width of one video clip)
                const calculateScrollAmount = () => {
                    const item = carousel.querySelector('.flex-none');
                    // item.offsetWidth is the width of the video item (which is w-full of the carousel container)
                    // We add 16px (0.25rem * 4 = 1rem = 16px, which is the space-x-4)
                    return item ? item.offsetWidth + 16 : carousel.offsetWidth; 
                };

                prevButton.addEventListener('click', () => {
                    carousel.scrollBy({
                        left: -calculateScrollAmount(),
                        behavior: 'smooth'
                    });
                });

                nextButton.addEventListener('click', () => {
                    carousel.scrollBy({
                        left: calculateScrollAmount(),
                        behavior: 'smooth'
                    });
                });
                
                // Re-create icons to ensure the new carousel buttons have their icons rendered
                lucide.createIcons();
            }
        });
        // ** END NEW JS **
    </script>

</body>
</html>
