import React, { useEffect, useRef, useState } from 'react';
import { motion, useScroll, useTransform, useSpring, useInView, useMotionValue, useAnimation } from 'framer-motion';
import '.App.css';

function App() {
  const [mousePosition, setMousePosition] = useState({ x 0, y 0 });
  const { scrollYProgress } = useScroll();
  
  useEffect(() = {
    const handleMouseMove = (e) = {
      setMousePosition({ x e.clientX, y e.clientY });
    };
    window.addEventListener('mousemove', handleMouseMove);
    return () = window.removeEventListener('mousemove', handleMouseMove);
  }, []);

  return (
    div className=relative w-full overflow-hidden bg-gradient-to-b from-slate-950 via-slate-900 to-slate-950
      { Mouse Spotlight Effect }
      motion.div
        className=pointer-events-none fixed inset-0 z-30 transition duration-300
        style={{
          background `radial-gradient(600px at ${mousePosition.x}px ${mousePosition.y}px, rgba(201, 168, 76, 0.08), transparent 80%)`
        }}
      

      { Animated Background Orbs }
      div className=fixed inset-0 overflow-hidden pointer-events-none
        motion.div
          className=absolute -top-48 -right-48 w-96 h-96 bg-amber-50020 rounded-full blur-3xl
          animate={{
            scale [1, 1.2, 1],
            x [0, 50, 0],
            y [0, -30, 0],
          }}
          transition={{ duration 20, repeat Infinity, ease easeInOut }}
        
        motion.div
          className=absolute top-12 -left-48 w-[500px] h-[500px] bg-blue-50010 rounded-full blur-3xl
          animate={{
            scale [1, 1.3, 1],
            x [0, -50, 0],
            y [0, 50, 0],
          }}
          transition={{ duration 25, repeat Infinity, ease easeInOut }}
        
        motion.div
          className=absolute bottom-0 right-14 w-[400px] h-[400px] bg-purple-50010 rounded-full blur-3xl
          animate={{
            scale [1, 1.1, 1],
            x [0, 30, 0],
            y [0, -40, 0],
          }}
          transition={{ duration 18, repeat Infinity, ease easeInOut }}
        
      div

      { Navigation }
      Navigation scrollYProgress={scrollYProgress} 

      { Hero Section }
      HeroSection 

      { About Section }
      AboutSection 

      { Expertise Section }
      ExpertiseSection 

      { Experience Section }
      ExperienceSection 

      { Skills Section }
      SkillsSection 

      { Certifications }
      CertificationsSection 

      { Contact Section }
      ContactSection 

      { Footer }
      Footer 

      { Floating Geometric Shapes }
      FloatingShapes 
    div
  );
}

 Navigation Component
const Navigation = ({ scrollYProgress }) = {
  const backgroundColor = useTransform(scrollYProgress, [0, 0.1], ['rgba(10, 22, 40, 0)', 'rgba(10, 22, 40, 0.95)']);
  
  return (
    motion.nav
      style={{ backgroundColor }}
      className=fixed top-0 left-0 right-0 z-50 backdrop-blur-xl border-b border-amber-50010
    
      div className=max-w-7xl mx-auto px-6 lgpx-12 py-5 flex items-center justify-between
