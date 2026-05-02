const CACHE_NAME = 'matchpro-v7.5.0';
const ASSETS_TO_CACHE = [
    './',
    './index.html',
    './manifest.json',
    './icon.svg',
    './COMPETITION_TEMPLATE.xlsx',
    'https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js',
    'https://cdnjs.cloudflare.com/ajax/libs/exceljs/4.3.0/exceljs.min.js'
];

self.addEventListener('install', (event) => {
    event.waitUntil(caches.open(CACHE_NAME).then((cache) => cache.addAll(ASSETS_TO_CACHE)));
    self.skipWaiting();
});

self.addEventListener('activate', (event) => {
    event.waitUntil(caches.keys().then((names) => Promise.all(names.map((n) => { 
        if(n !== CACHE_NAME) return caches.delete(n); 
    }))));
    self.clients.claim();
});

self.addEventListener('fetch', (event) => {
    event.respondWith(caches.match(event.request).then((res) => res || fetch(event.request)));
});