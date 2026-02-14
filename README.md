# Trinexiss-website
Company code 

import React, { Suspense, lazy } from 'react';
import { HashRouter as Router, Routes, Route } from 'react-router-dom';
import { Layout } from './components/Layout';
import Chatbot from './components/Chatbot';
import WhatsAppButton from './components/WhatsAppButton';

// Lazy load pages for better performance
const Home = lazy(() => import('./pages/Home'));
const About = lazy(() => import('./pages/About'));
const Services = lazy(() => import('./pages/Services'));
const Jobs = lazy(() => import('./pages/Jobs'));
const CandidatePortal = lazy(() => import('./pages/CandidatePortal'));
const EmployerPortal = lazy(() => import('./pages/EmployerPortal'));
const Contact = lazy(() => import('./pages/Contact'));

const LoadingScreen = () => (
  <div className="flex items-center justify-center min-h-screen bg-slate-50">
    <div className="flex flex-col items-center">
      <div className="w-12 h-12 border-4 border-blue-600 border-t-transparent rounded-full animate-spin mb-4"></div>
      <p className="text-slate-500 font-medium animate-pulse">Initializing Trinexiss...</p>
    </div>
  </div>
);

const App: React.FC = () => {
  return (
    <Router>
      <Layout>
        <Suspense fallback={<LoadingScreen />}>
          <Routes>
            <Route path="/" element={<Home />} />
            <Route path="/about" element={<About />} />
            <Route path="/services" element={<Services />} />
            <Route path="/jobs" element={<Jobs />} />
            <Route path="/candidate-portal" element={<CandidatePortal />} />
            <Route path="/employer-portal" element={<EmployerPortal />} />
            <Route path="/contact" element={<Contact />} />
          </Routes>
        </Suspense>
        <Chatbot />
        <WhatsAppButton />
      </Layout>
    </Router>
  );
};

export default App;
