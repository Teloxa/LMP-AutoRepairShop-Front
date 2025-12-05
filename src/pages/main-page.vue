<template>
  <NavbarContent />

  <div>
    <!-- SECTION 1: HERO SECTION -->
    <div class="relative h-[60vh] bg-gray-900 flex items-center justify-center overflow-hidden">
      <!-- Background layer with image (resolved by Vite via import) -->
      <div
        class="absolute inset-0 bg-cover bg-center"
        :style="{ backgroundImage: `url(${bgIndex})`, opacity: 0.7 }"
      ></div>

      <!-- Main content -->
      <div class="relative z-10 text-center text-white p-6">
        <h1 class="text-4xl sm:text-5xl font-extrabold mb-4">Your vehicle, in our hands</h1>
        <p class="text-lg sm:text-xl mb-8 font-light max-w-2xl mx-auto">
          Schedule your next service and ensure your car's optimal performance with Autofix.
        </p>

        <!-- Primary button (Call to Action) -->
        <button
          class="px-8 py-3 font-bold bg-white text-sky-700 border border-sky-600 rounded-full shadow-lg hover:bg-sky-50 hover:text-sky-800"
          @click="$router.push('/clients')"
        >
          Make a quote
        </button>
      </div>
    </div>

    <!-- SECTION 2: FEATURED SERVICES (4 items) -->
    <div class="py-16 bg-white">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold text-center mb-12 text-gray-800">Our Key Services</h2>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <!-- Card 1: Oil Change -->
          <ServiceCard
            title="1. Oil Change"
            description="Vital for engine health. We use high-quality lubricants to protect against wear and maintain efficiency."
            imagePlaceholder="https://d26qplkpp6t30l.cloudfront.net/wp-content/uploads/2019/01/22092032/oil-change-explained.jpg"
          />

          <!-- Card 2: Brakes -->
          <ServiceCard
            title="2. Brakes"
            description="Inspection and replacement of pads, rotors and brake fluid. We ensure your safety with a reliable braking system."
            imagePlaceholder="https://pictures.dealer.com/j/jungeautomotivegroup/0904/b05d0de8bb6dda7e5969c5752836948fx.jpg"
          />

          <!-- Card 3: Tune-up -->
          <ServiceCard
            title="3. Tune-up"
            description="Improves performance, reduces emissions and optimizes fuel consumption. Includes spark plugs, filters and essential fluids check."
            imagePlaceholder="https://omegaautocare.com/wp-content/uploads/2023/02/car-tune-up-basics.jpg"
          />

          <!-- Card 4: General Maintenance -->
          <ServiceCard
            title="4. General Maintenance"
            description="Comprehensive 100-point inspection, including fluid levels, tires, suspension and electrical system. Prevention is the best investment."
            imagePlaceholder="https://di-sitebuilder-assets.dealerinspire.com/Ford/requiredPages/GeneralMaintenance/hero.jpg"
          />
        </div>
      </div>
    </div>

    <!-- SECTION 3: ABOUT THE SERVICE -->
    <div>
      <div class="mx-auto px-4 py-16 bg-[#101628]">
        <div class="md:flex md:items-center md:gap-8">
          <div class="md:w-1/2 mb-8 md:mb-0">
            <img
              src="https://carsautorepairservice.com/wp-content/uploads/2022/10/CARS-Automotive-Repair-Jenison_2.jpg"
              alt="About Autofix"
              class="w-full max-w-lg mx-auto h-auto rounded-lg"
            />
          </div>

          <div class="md:w-1/2">
            <h1 class="text-3xl font-bold mb-4 text-white">About the service</h1>
            <p class="text-slate-300 mb-6 leading-relaxed">
              Keep your vehicle safe and responsive with our comprehensive brake service. Your
              brakes are one of the most critical safety systems in your vehicle, and regular
              maintenance is essential for optimal performance. Our certified technicians use
              state-of-the-art diagnostic equipment to ensure your braking system meets manufacturer
              specifications and delivers reliable stopping power when you need it most.
            </p>
            <h2 class="text-3xl font-bold mb-4 text-white">Why Choose Autofix?</h2>
            <p class="text-slate-300 mb-6 leading-relaxed">
              At Autofix, we prioritize your vehicle's health and your peace of mind. Our team of
              certified technicians uses state-of-the-art equipment to provide top-notch service.
              From routine maintenance to complex repairs, we ensure quality workmanship and
              transparent pricing. Experience convenience with our easy online scheduling and
              exceptional customer service.
            </p>
            <ul class="list-disc list-inside text-slate-300 space-y-2 leading-relaxed">
              <li>Certified and experienced technicians</li>
              <li>Use of high-quality parts and fluids</li>
              <li>Comprehensive vehicle inspections</li>
              <li>Transparent pricing with no hidden fees</li>
              <li>Convenient online scheduling</li>
            </ul>
          </div>
        </div>
      </div>
    </div>

    <!-- SECTION 4: PARTNERS -->
    <div class="py-16 bg-slate-50">
      <div class="container mx-auto px-4">
        <h2 class="text-3xl font-bold text-center mb-12 text-gray-800">Our Trusted Partners</h2>
        <div class="flex flex-wrap items-center justify-center gap-6 py-8">
          <img
            src="//d9hhrg4mnvzow.cloudfront.net/cinch.io/tire-lp-google/20587a81-1_104l04j03t01l00h01i028.png"
            alt=""
            class="w-20 md:w-28 lg:w-36 h-auto object-contain opacity-90"
            loading="lazy"
            srcset="
              //d9hhrg4mnvzow.cloudfront.net/cinch.io/tire-lp-google/20587a81-1_104l04j03t01l00h01i028.png 1x,
              //d9hhrg4mnvzow.cloudfront.net/cinch.io/tire-lp-google/20587a81-1_109609207m03600y030028.png 2x,
              //d9hhrg4mnvzow.cloudfront.net/cinch.io/tire-lp-google/20587a81-1_10dr0dl0bf04r01f04i028.png 3x
            "
          />

          <img
            src="//d9hhrg4mnvzow.cloudfront.net/cinch.io/tire-lp-google/d99a7cf4-jiffy-lube-vector-logo.svg"
            alt="Jiffy Lube logo"
            class="w-20 md:w-28 lg:w-36 h-auto object-contain opacity-90"
            loading="lazy"
          />

          <img
            src="//d9hhrg4mnvzow.cloudfront.net/cinch.io/tire-lp-google/737ad279-logo-wht-300x167.png"
            alt="Partner logo 3"
            class="w-20 md:w-28 lg:w-36 h-auto object-contain opacity-90"
            loading="lazy"
          />

          <img
            src="//d9hhrg4mnvzow.cloudfront.net/cinch.io/tire-lp-google/018d267e-victory-lane-logo.webp"
            alt="Victory Lane logo"
            class="w-20 md:w-28 lg:w-36 h-auto object-contain opacity-90"
            loading="lazy"
          />

          <img
            src="//d9hhrg4mnvzow.cloudfront.net/cinch.io/tire-lp-google/d9fc2df7-chapel-hill-tire-nc-logo.svg"
            alt="Chapel Hill Tire logo"
            class="w-20 md:w-28 lg:w-36 h-auto object-contain opacity-90"
            loading="lazy"
          />

          <img
            src="//d9hhrg4mnvzow.cloudfront.net/cinch.io/tire-lp-google/30f4e25e-oilstop-logo_104y00z000000000000028.png"
            alt="Partner logo 5"
            class="w-20 md:w-28 lg:w-36 h-auto object-contain opacity-90"
            loading="lazy"
            srcset="
              //d9hhrg4mnvzow.cloudfront.net/cinch.io/tire-lp-google/30f4e25e-oilstop-logo_104y00z000000000000028.png 1x,
              //d9hhrg4mnvzow.cloudfront.net/cinch.io/tire-lp-google/30f4e25e-oilstop-logo_109w01y000000000000028.png 2x,
              //d9hhrg4mnvzow.cloudfront.net/cinch.io/tire-lp-google/30f4e25e-oilstop-logo_1000000000000000000028.png 3x
            "
          />

          <img
            src="//d9hhrg4mnvzow.cloudfront.net/cinch.io/tire-lp-google/9b7d7b95-master-auto-tech-icon.svg"
            alt="Partner logo 6"
            class="w-20 md:w-28 lg:w-36 h-auto object-contain opacity-90"
            loading="lazy"
          />
        </div>
      </div>
    </div>

    <!-- SECTION 5: FOOTER -->
    <footer class="bg-slate-900 text-slate-200 mt-8">
      <div class="container mx-auto px-4 py-12">
        <!-- Top grid: 5 columns on desktop, stacks on mobile -->
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-5 gap-8">
          <!-- Contact Information -->
          <div class="container lg:col-span-2">
            <h3 class="text-white font-semibold text-lg mb-4">Contact</h3>
            <ul class="space-y-2 text-sm">
              <li class="flex items-start gap-2">
                <span class="mt-0.5">Hours:</span>
                <span>Mon–Fri 7:00 AM–6:00 PM, Sat 8:00 AM–4:00 PM</span>
              </li>
              <li class="flex items-start gap-2">
                <span class="mt-0.5">Address:</span>
                <span>1234 Main St, City, ST 00000</span>
              </li>
              <li class="flex items-start gap-2">
                <span class="mt-0.5">Phone:</span>
                <a href="tel:+15551234567" class="text-sky-400 hover:text-sky-300"
                  >(555) 123-4567</a
                >
              </li>
              <li class="flex items-start gap-2">
                <span class="mt-0.5">Email:</span>
                <a href="mailto:service@autofix.com" class="text-sky-400 hover:text-sky-300"
                  >service@autofix.com</a
                >
              </li>
            </ul>
          </div>

          <!-- Popular Services -->
          <div>
            <h3 class="text-white font-semibold text-lg mb-4">Popular Services</h3>
            <ul class="space-y-2 text-sm">
              <li><a href="#" class="hover:text-white transition">Brake Service</a></li>
              <li><a href="#" class="hover:text-white transition">Oil Changes</a></li>
              <li><a href="#" class="hover:text-white transition">Engine Repair</a></li>
              <li><a href="#" class="hover:text-white transition">Tire Services</a></li>
              <li><a href="#" class="hover:text-white transition">AC Repair</a></li>
            </ul>
          </div>

          <!-- Customer Resources -->
          <div>
            <h3 class="text-white font-semibold text-lg mb-4">Customer Resources</h3>
            <ul class="space-y-2 text-sm">
              <li><a href="#" class="hover:text-white transition">Service Tips / Blog</a></li>
              <li><a href="#" class="hover:text-white transition">FAQ</a></li>
              <li><a href="#" class="hover:text-white transition">Financing</a></li>
              <li><a href="#" class="hover:text-white transition">Warranty Info</a></li>
            </ul>
          </div>
        </div>

        <!-- Divider -->
        <hr class="my-8 border-slate-700" />

        <!-- Payment methods and CTAs -->
        <div class="flex flex-col lg:flex-row items-center justify-between gap-4">
          <div class="flex items-center gap-2 text-sm text-slate-300">
            <span>Payment Accepted:</span>
            <span
              class="inline-flex items-center gap-1 px-2 py-1 rounded bg-slate-800 border border-slate-700"
              >Visa</span
            >
            <span
              class="inline-flex items-center gap-1 px-2 py-1 rounded bg-slate-800 border border-slate-700"
              >Mastercard</span
            >
            <span
              class="inline-flex items-center gap-1 px-2 py-1 rounded bg-slate-800 border border-slate-700"
              >AmEx</span
            >
            <span
              class="inline-flex items-center gap-1 px-2 py-1 rounded bg-slate-800 border border-slate-700"
              >Digital Wallets</span
            >
          </div>
        </div>

        <!-- Legal -->
        <div
          class="mt-8 flex flex-col lg:flex-row items-center justify-between gap-3 text-xs text-slate-400"
        >
          <div class="flex items-center gap-3">
            <a href="#" class="hover:text-white transition">Privacy Policy</a>
            <a href="#" class="hover:text-white transition">Terms of Service</a>
          </div>
          <div>&copy; {{ new Date().getFullYear() }} Autofix. All rights reserved.</div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
import NavbarContent from '@/components/ui/NavbarContent.vue'
import ServiceCard from '@/components/ui/ServiceCard.vue'
import bgIndex from '@/assets/bg-index.jpg'

export default {
  components: { NavbarContent, ServiceCard },
  data() {
    return { bgIndex }
  },
}
</script>
