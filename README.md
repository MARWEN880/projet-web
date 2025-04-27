// src/App.js
import React, { useState, useEffect } from 'react';
import './App.css';
import { Camera, Menu, X, ChevronRight, ShoppingCart, Phone, Mail, MapPin, Facebook, Instagram, Search, User } from 'lucide-react';

function App() {
  const [isMenuOpen, setIsMenuOpen] = useState(false);
  const [isFixed, setIsFixed] = useState(false);

  useEffect(() => {
    const handleScroll = () => {
      if (window.scrollY > 100) {
        setIsFixed(true);
      } else {
        setIsFixed(false);
      }
    };

    window.addEventListener('scroll', handleScroll);
    return () => {
      window.removeEventListener('scroll', handleScroll);
    };
  }, []);

  return (
    <div className="min-h-screen flex flex-col">
      {/* Top Bar */}
      <div className="bg-black text-white py-2 hidden md:block">
        <div className="container mx-auto px-4 flex justify-between items-center">
          <div className="flex items-center space-x-4">
            <div className="flex items-center">
              <Phone className="h-4 w-4 mr-2" />
              <span className="text-sm">+33 1 23 45 67 89</span>
            </div>
            <div className="flex items-center">
              <Mail className="h-4 w-4 mr-2" />
              <span className="text-sm">contact@bk-cam.com</span>
            </div>
          </div>
          <div className="flex items-center space-x-4">
            <a href="#" className="text-sm">Mon compte</a>
            <a href="#" className="text-sm">Panier</a>
            <div className="flex space-x-2">
              <a href="#">
                <Facebook className="h-4 w-4" />
              </a>
              <a href="#">
                <Instagram className="h-4 w-4" />
              </a>
            </div>
          </div>
        </div>
      </div>

      {/* Header */}
      <header className={`bg-white text-black ${isFixed ? 'fixed top-0 left-0 right-0 shadow-md z-50' : ''}`}>
        <div className="container mx-auto px-4 py-4 flex justify-between items-center">
          <div className="flex items-center">
            <img src="/api/placeholder/180/60" alt="BK-CAM Logo" className="h-10" />
          </div>
          
          {/* Search Bar - Desktop */}
          <div className="hidden md:block flex-grow mx-8">
            <div className="relative">
              <input 
                type="text" 
                placeholder="Rechercher des produits..." 
                className="w-full py-2 px-4 border border-gray-300 rounded-full" 
              />
              <button className="absolute right-0 top-0 bottom-0 bg-red-600 text-white px-4 rounded-r-full">
                <Search className="h-5 w-5" />
              </button>
            </div>
          </div>
          
          {/* Right Menu - Desktop */}
          <div className="hidden md:flex items-center space-x-6">
            <a href="#" className="flex items-center">
              <User className="h-5 w-5 mr-1" />
              <span>Compte</span>
            </a>
            <a href="#" className="flex items-center">
              <ShoppingCart className="h-5 w-5 mr-1" />
              <span>Panier</span>
            </a>
          </div>
          
          {/* Mobile menu button */}
          <button 
            className="md:hidden"
            onClick={() => setIsMenuOpen(!isMenuOpen)}
          >
            {isMenuOpen ? <X /> : <Menu />}
          </button>
        </div>
        
        {/* Main Navigation */}
        <nav className="hidden md:block bg-red-600 text-white">
          <div className="container mx-auto px-4">
            <ul className="flex">
              <li className="group relative">
                <a href="#" className="block px-4 py-3 hover:bg-red-700">Accueil</a>
              </li>
              <li className="group relative">
                <a href="#" className="block px-4 py-3 hover:bg-red-700">Caméras</a>
                <div className="hidden group-hover:block absolute left-0 bg-white text-black shadow-lg z-10 w-48">
                  <a href="#" className="block px-4 py-2 hover:bg-gray-100">Caméras IP</a>
                  <a href="#" className="block px-4 py-2 hover:bg-gray-100">Caméras analogiques</a>
                  <a href="#" className="block px-4 py-2 hover:bg-gray-100">Caméras PTZ</a>
                </div>
              </li>
              <li className="group relative">
                <a href="#" className="block px-4 py-3 hover:bg-red-700">Enregistreurs</a>
                <div className="hidden group-hover:block absolute left-0 bg-white text-black shadow-lg z-10 w-48">
                  <a href="#" className="block px-4 py-2 hover:bg-gray-100">NVR</a>
                  <a href="#" className="block px-4 py-2 hover:bg-gray-100">DVR</a>
                </div>
              </li>
              <li className="group relative">
                <a href="#" className="block px-4 py-3 hover:bg-red-700">Accessoires</a>
              </li>
              <li className="group relative">
                <a href="#" className="block px-4 py-3 hover:bg-red-700">Kits</a>
              </li>
              <li className="group relative">
                <a href="#" className="block px-4 py-3 hover:bg-red-700">Services</a>
              </li>
              <li className="group relative">
                <a href="#" className="block px-4 py-3 hover:bg-red-700">À propos</a>
              </li>
              <li className="group relative">
                <a href="#" className="block px-4 py-3 hover:bg-red-700">Contact</a>
              </li>
            </ul>
          </div>
        </nav>
        
        {/* Mobile Nav */}
        {isMenuOpen && (
          <div className="md:hidden">
            <div className="p-4">
              <div className="relative mb-4">
                <input 
                  type="text" 
                  placeholder="Rechercher des produits..." 
                  className="w-full py-2 px-4 border border-gray-300 rounded-full" 
                />
                <button className="absolute right-0 top-0 bottom-0 bg-red-600 text-white px-4 rounded-r-full">
                  <Search className="h-5 w-5" />
                </button>
              </div>
            </div>
            <nav className="bg-red-600 text-white">
              <a href="#" className="block px-4 py-3 hover:bg-red-700">Accueil</a>
              <a href="#" className="block px-4 py-3 hover:bg-red-700 border-t border-red-500">Caméras</a>
              <a href="#" className="block px-4 py-3 hover:bg-red-700 border-t border-red-500">Enregistreurs</a>
              <a href="#" className="block px-4 py-3 hover:bg-red-700 border-t border-red-500">Accessoires</a>
              <a href="#" className="block px-4 py-3 hover:bg-red-700 border-t border-red-500">Kits</a>
              <a href="#" className="block px-4 py-3 hover:bg-red-700 border-t border-red-500">Services</a>
              <a href="#" className="block px-4 py-3 hover:bg-red-700 border-t border-red-500">À propos</a>
              <a href="#" className="block px-4 py-3 hover:bg-red-700 border-t border-red-500">Contact</a>
              <a href="#" className="block px-4 py-3 hover:bg-red-700 border-t border-red-500">Mon compte</a>
              <a href="#" className="block px-4 py-3 hover:bg-red-700 border-t border-red-500">Panier</a>
            </nav>
          </div>
        )}
      </header>

      {/* Hero Slider */}
      <section className={`bg-gray-100 pt-4 pb-8 ${isFixed ? 'mt-32' : ''}`}>
        <div className="container mx-auto px-4">
          <div className="relative bg-gray-800 h-96 rounded-lg overflow-hidden">
            <div className="absolute inset-0 flex items-center">
              <img src="/api/placeholder/1200/500" alt="Slider Image" className="w-full object-cover" />
            </div>
            <div className="absolute inset-0 bg-black bg-opacity-40 flex items-center">
              <div className="mx-12 text-white max-w-lg">
                <h2 className="text-4xl font-bold mb-4">Solutions de Vidéosurveillance Professionnelles</h2>
                <p className="text-xl mb-8">Systèmes de vidéosurveillance de haute qualité pour votre sécurité</p>
                <button className="bg-red-600 text-white px-8 py-3 rounded font-bold hover:bg-red-700">
                  Découvrir nos produits
                </button>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Categories */}
      <section className="py-12">
        <div className="container mx-auto px-4">
          <h2 className="text-3xl font-bold text-center mb-8">Catégories populaires</h2>
          
          <div className="grid grid-cols-2 md:grid-cols-4 gap-4">
            {[
              {title: "Caméras IP", image: "/api/placeholder/300/200"},
              {title: "Enregistreurs NVR", image: "/api/placeholder/300/200"},
              {title: "Kits de surveillance", image: "/api/placeholder/300/200"},
              {title: "Accessoires", image: "/api/placeholder/300/200"}
            ].map((category, index) => (
              <div key={index} className="group relative rounded-lg overflow-hidden shadow-md">
                <img src={category.image} alt={category.title} className="w-full h-48 object-cover" />
                <div className="absolute inset-0 bg-gradient-to-t from-black to-transparent opacity-70"></div>
                <div className="absolute bottom-0 left-0 right-0 p-4">
                  <h3 className="text-white font-bold text-xl">{category.title}</h3>
                </div>
                <div className="absolute inset-0 bg-red-600 bg-opacity-80 opacity-0 group-hover:opacity-100 transition-opacity flex items-center justify-center">
                  <button className="bg-white text-red-600 px-4 py-2 rounded font-medium">
                    Voir les produits
                  </button>
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Featured Products */}
      <section className="bg-gray-100 py-12">
        <div className="container mx-auto px-4">
          <div className="flex justify-between items-center mb-8">
            <h2 className="text-3xl font-bold">Produits populaires</h2>
            <a href="#" className="text-red-600 font-medium hover:text-red-700">Voir tous les produits</a>
          </div>
          
          <div className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-6">
            {[1, 2, 3, 4].map((item) => (
              <div key={item} className="bg-white rounded-lg overflow-hidden shadow-md hover:shadow-lg transition-shadow">
                <div className="relative">
                  <img src="/api/placeholder/300/300" alt={`Produit ${item}`} className="w-full h-64 object-contain p-4" />
                  <div className="absolute top-2 right-2">
                    <span className="bg-red-600 text-white text-xs px-2 py-1 rounded">-15%</span>
                  </div>
                </div>
                <div className="p-4">
                  <h3 className="font-bold text-lg mb-2">Caméra IP HD {item}MP</h3>
                  <div className="flex justify-between items-center mb-2">
                    <div>
                      <span className="text-red-600 font-bold text-lg">149.99€</span>
                      <span className="text-gray-500 line-through text-sm ml-2">179.99€</span>
                    </div>
                    <div className="flex items-center text-yellow-500">
                      {"★".repeat(4)}{"☆".repeat(1)}
                    </div>
                  </div>
                  <p className="text-gray-600 text-sm mb-4">Caméra de surveillance haute définition avec vision nocturne et détection de mouvement</p>
                  <button className="bg-red-600 text-white w-full py-2 rounded font-medium hover:bg-red-700 flex items-center justify-center">
                    <ShoppingCart className="w-5 h-5 mr-2" />
                    Ajouter au panier
                  </button>
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Banner */}
      <section className="py-12">
        <div className="container mx-auto px-4">
          <div className="relative bg-gray-800 rounded-lg overflow-hidden">
            <div className="md:flex">
              <div className="md:w-1/2">
                <img src="/api/placeholder/600/400" alt="Promo Banner" className="w-full h-64 md:h-full object-cover" />
              </div>
              <div className="md:w-1/2 p-8 md:p-12 flex items-center">
                <div className="text-white">
                  <h2 className="text-3xl font-bold mb-4">Installation professionnelle à partir de 99€</h2>
                  <p className="mb-6">Confiez l'installation de votre système de vidéosurveillance à nos experts pour une sécurité optimale.</p>
                  <button className="bg-red-600 text-white px-6 py-3 rounded font-bold hover:bg-red-700">
                    En savoir plus
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Top-Selling Products */}
      <section className="py-12">
        <div className="container mx-auto px-4">
          <div className="flex justify-between items-center mb-8">
            <h2 className="text-3xl font-bold">Meilleures ventes</h2>
            <a href="#" className="text-red-600 font-medium hover:text-red-700">Voir toutes les meilleures ventes</a>
          </div>
          
          <div className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-6">
            {[1, 2, 3, 4].map((item) => (
              <div key={item} className="bg-white rounded-lg overflow-hidden shadow-md hover:shadow-lg transition-shadow">
                <div className="relative">
                  <img src="/api/placeholder/300/300" alt={`Produit ${item}`} className="w-full h-64 object-contain p-4" />
                  {item === 1 && (
                    <div className="absolute top-2 right-2">
                      <span className="bg-green-600 text-white text-xs px-2 py-1 rounded">Top vente</span>
                    </div>
                  )}
                </div>
                <div className="p-4">
                  <h3 className="font-bold text-lg mb-2">Kit Surveillance {item} Caméras</h3>
                  <div className="flex justify-between items-center mb-2">
                    <div>
                      <span className="text-red-600 font-bold text-lg">299.99€</span>
                    </div>
                    <div className="flex items-center text-yellow-500">
                      {"★".repeat(5)}{"☆".repeat(0)}
                    </div>
                  </div>
                  <p className="text-gray-600 text-sm mb-4">Kit complet avec enregistreur et {item} caméras HD, installation facile</p>
                  <button className="bg-red-600 text-white w-full py-2 rounded font-medium hover:bg-red-700 flex items-center justify-center">
                    <ShoppingCart className="w-5 h-5 mr-2" />
                    Ajouter au panier
                  </button>
                </div>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Features */}
      <section className="bg-gray-100 py-12">
        <div className="container mx-auto px-4">
          <div className="grid grid-cols-1 md:grid-cols-4 gap-8">
            <div className="flex flex-col items-center text-center">
              <div className="bg-red-600 text-white p-4 rounded-full w-16 h-16 flex items-center justify-center mb-4">
                <svg xmlns="http://www.w3.org/2000/svg" className="h-8 w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M5 13l4 4L19 7" />
                </svg>
              </div>
              <h3 className="font-bold text-lg mb-2">Qualité garantie</h3>
              <p className="text-gray-600">Produits de haute qualité sélectionnés pour leur fiabilité</p>
            </div>
            
            <div className="flex flex-col items-center text-center">
              <div className="bg-red-600 text-white p-4 rounded-full w-16 h-16 flex items-center justify-center mb-4">
                <svg xmlns="http://www.w3.org/2000/svg" className="h-8 w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M20 7l-8 4-8-4V18l8 4 8-4V7z" />
                </svg>
              </div>
              <h3 className="font-bold text-lg mb-2">Livraison rapide</h3>
              <p className="text-gray-600">Expédition sous 24h pour toutes vos commandes</p>
            </div>
            
            <div className="flex flex-col items-center text-center">
              <div className="bg-red-600 text-white p-4 rounded-full w-16 h-16 flex items-center justify-center mb-4">
                <svg xmlns="http://www.w3.org/2000/svg" className="h-8 w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M3 10h18M7 15h1m4 0h1m-7 4h12a3 3 0 003-3V8a3 3 0 00-3-3H6a3 3 0 00-3 3v8a3 3 0 003 3z" />
                </svg>
              </div>
              <h3 className="font-bold text-lg mb-2">Paiement sécurisé</h3>
              <p className="text-gray-600">Transactions sécurisées et multiples options de paiement</p>
            </div>
            
            <div className="flex flex-col items-center text-center">
              <div className="bg-red-600 text-white p-4 rounded-full w-16 h-16 flex items-center justify-center mb-4">
                <svg xmlns="http://www.w3.org/2000/svg" className="h-8 w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={2} d="M18.364 5.636l-3.536 3.536m0 5.656l3.536 3.536M9.172 9.172L5.636 5.636m3.536 9.192l-3.536 3.536M21 12a9 9 0 11-18 0 9 9 0 0118 0zm-5 0a4 4 0 11-8 0 4 4 0 018 0z" />
                </svg>
              </div>
              <h3 className="font-bold text-lg mb-2">Support technique</h3>
              <p className="text-gray-600">Assistance technique disponible 7j/7 pour vous accompagner</p>
            </div>
          </div>
        </div>
      </section>

      {/* Newsletter */}
      <section className="py-12 bg-red-600 text-white">
        <div className="container mx-auto px-4">
          <div className="md:flex items-center justify-between">
            <div className="md:w-1/2 mb-6 md:mb-0">
              <h2 className="text-3xl font-bold mb-2">Recevez nos offres exclusives</h2>
              <p>Inscrivez-vous à notre newsletter et bénéficiez de 10% de réduction sur votre première commande</p>
            </div>
            <div className="md:w-1/2">
              <form className="flex flex-col md:flex-row">
                <input 
                  type="email" 
                  placeholder="Votre adresse email" 
                  className="flex-grow px-4 py-3 rounded-l md:rounded-r-none text-black mb-2 md:mb-0" 
                />
                <button className="bg-black text-white px-6 py-3 font-bold rounded-r md:rounded-l-none hover:bg-gray-800">
                  S'inscrire
                </button>
              </form>
            </div>
          </div>
        </div>
      </section>

      {/* Footer */}
      <footer className="bg-gray-900 text-white pt-12 pb-6">
        <div className="container mx-auto px-4">
          <div className="grid grid-cols-1 md:grid-cols-4 gap-8 mb-8">
            <div>
              <img src="/api/placeholder/180/60" alt="BK-CAM Logo" className="h-8 mb-4" />
              <p className="text-gray-400 mb-4">Solutions de vidéosurveillance professionnelles pour entreprises et particuliers.</p>
              <div className="flex space-x-4">
                <a href="#" className="text-gray-400 hover:text-white">
                  <Facebook className="h-6 w-6" />
                </a>
                <a href="#" className="text-gray-400 hover:text-white">
                  <Instagram className="h-6 w-6" />
                </a>
              </div>
            </div>
            
            <div>
              <h3 className="text-lg font-bold mb-4">Produits</h3>
              <ul className="space-y-2 text-gray-400">
                <li><a href="#" className="hover:text-white">Caméras IP</a></li>
                <li><a href="#" className="hover:text-white">Caméras analogiques</a></li>
                <li><a href="#" className="hover:text-white">Enregistreurs NVR/DVR</a></li>
                <li><a href="#" className="hover:text-white">Kits de surveillance</a></li>
                <li><a href="#" className="hover:text-white">Accessoires</a></li>
              </ul>
            </div>
            
            <div>
              <h3 className="text-lg font-bold mb-4">Services</h3>
              <ul className="space-y-2 text-gray-400">
                <li><a href="#" className="hover:text-white">Installation</a></li>
                <li><a href="#" className="hover:text-white">Maintenance</a></li>
                <li><a href="#" className="hover:text-white">Support technique</a></li>
                <li><a href="#" className="hover:text-white">Demande de devis</a></li>
                <li><a href="#" className="hover:text-white">FAQ</a></li>
              </ul>
            </div>
            
            <div>
              <h3 className="text-lg font-bold mb-4">Contact</h3>
              <ul className="space-y-2 text-gray-400">
                <li className="flex items-start">
                  <MapPin className="h-5 w-5 mr-2 mt-1 text-red-600" />
                  <span>123 Rue de la Sécurité, 75000 Paris</span>
                </li>
                <li className="flex items-center">
                  <Phone className="h-5 w-5 mr-2 text-red-600" />
                  <a href="tel:+33123456789" className="hover:text-white">+33 1 23 45 67 89</a>
                </li>
                <li className="flex items-center">
                  <Mail className="h-5 w-5 mr-2 text-red-600" />
                  <a href="mailto:contact@bk-cam.com" className="hover:text-white">contact@bk-cam.com</a>
                </li>
              </ul>
            </div>
          </div>
          
          <div className="border-t border-gray-800 pt-6 text-center text-gray-400">
            <div className="mb-4">
              <a href="#" className="mx-2 hover:text-white">Conditions générales</a>
              <a href="#" className="mx-2 hover:text-white">Politique de confidentialité</a>
              <a href="#" className="mx-2 hover:text-white">Livraison</a>
              <a href="#" className="mx-2 hover:text-white">Retours</a>
            </div>
            <p>&copy; {new Date().getFullYear()} BK-CAM. Tous droits réservés.</p>
          </div>
        </div>
      </footer>
    </div>
  );
}

export default App;

// src/index.js
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);

// src/App.css
/* Effets de transition */
.transition-opacity {
  transition: opacity 0.3s ease;
}

.transition-shadow {
  transition: box-shadow 0.3s ease;
}

/* Vous pouvez ajouter des styles personnalisés supplémentaires ici */

// src/index.css
@tailwind base;
@tailwind components;
@tailwind utilities;

body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen',
    'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

/* Tailwind config */
// tailwind.config.js
module.exports = {
  content: ["./src/**/*.{js,jsx,ts,tsx}"],
  theme: {
    extend: {
      colors: {
        red: {
          600: '#d32f2f', // Couleur principale BK-CAM
          700: '#b71c1c', // Couleur hover
        }
      }
    },
  },
  plugins: [],
}
