// Nama cache unik untuk aplikasi absensi.
const CACHE_NAME = 'absensi-penyetan';

// Daftar lengkap file yang akan disimpan di cache.
const URLS_TO_CACHE = [
'/',
'index.html',

// File dari dalam folder 'favicon (1)'
'favicon (1)/site.webmanifest',
'favicon (1)/favicon.ico',
'favicon (1)/favicon.svg',
'favicon (1)/apple-touch-icon.png',
'favicon (1)/favicon-96x96.png',
'favicon (1)/web-app-manifest-192x192.png',
'favicon (1)/web-app-manifest-512x512.png',

// File eksternal (CDN) yang digunakan
'https://cdn.tailwindcss.com',
'https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap',
'https://unpkg.com/@phosphor-icons/web',
'https://raw.githubusercontent.com/Bukhori1/Aps/refs/heads/main/BackgroundEraser_20250715_125113431.jpg'
];

// Event 'install': Menyimpan file ke cache.
self.addEventListener('install', (event) => {
event.waitUntil(
caches.open(CACHE_NAME)
.then((cache) => {
console.log('Cache dibuka, menambahkan file inti aplikasi absensi');
return cache.addAll(URLS_TO_CACHE);
})
);
});

// Event 'fetch': Menyajikan file dari cache jika offline.
self.addEventListener('fetch', (event) => {
event.respondWith(
caches.match(event.request)
.then((response) => {
return response || fetch(event.request);
})
);
});

// Event 'activate': Membersihkan cache lama.
self.addEventListener('activate', (event) => {
const cacheWhitelist = [CACHE_NAME];
event.waitUntil(
caches.keys().then((cacheNames) => {
return Promise.all(
cacheNames.map((cacheName) => {
if (cacheWhitelist.indexOf(cacheName) === -1) {
return caches.delete(cacheName);
}
})
);
})
);
});