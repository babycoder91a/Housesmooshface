<footer>
  <a href="https://github.com/yourusername/your-repo-name" target="_blank" rel="noopener noreferrer">
    View Source on GitHub
  </a>
</footer>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap");

body {
  margin: 0;
  font-family: "Poppins", sans-serif;
  background: linear-gradient(135deg, #a1c4fd 0%, #c2e9fb 100%);
  background-size: 200% 200%;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  animation: gradientShift 8s ease infinite;
  overflow: hidden;
}

@keyframes gradientShift {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

.App {
  position: relative;
  background: rgba(255, 255, 255, 0.15);
  backdrop-filter: blur(14px);
  border-radius: 20px;
  padding: 40px;
  box-shadow: 0 0 30px rgba(0, 255, 255, 0.4), 0 0 50px rgba(255, 0, 255, 0.3);
  text-align: center;
  color: #fff;
  width: 90%;
  max-width: 500px;
  animation: fadeIn 1.2s ease-in-out, pulseGlow 2s infinite alternate;
  border: 3px solid transparent;
  background-clip: padding-box;
  overflow: visible;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes pulseGlow {
  0% {
    box-shadow: 0 0 20px rgba(0, 255, 255, 0.2), 0 0 40px rgba(255, 0, 255, 0.2);
  }
  100% {
    box-shadow: 0 0 40px rgba(0, 255, 255, 0.6), 0 0 60px rgba(255, 0, 255, 0.4);
  }
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 20px;
  color: #ffffff;
  text-shadow: 0 0 10px #00e0ff, 0 0 20px #ff8af0;
  animation: shimmer 1.5s infinite alternate, textPulse 3s ease-in-out infinite;
}

@keyframes shimmer {
  from {
    text-shadow: 0 0 10px #00e0ff, 0 0 20px #ff8af0;
  }
  to {
    text-shadow: 0 0 20px #ff8af0, 0 0 30px #00e0ff;
  }
}

@keyframes textPulse {
  0%, 100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.05);
  }
}

button {
  background: linear-gradient(45deg, #ff8af0, #00e0ff);
  color: white;
  border: none;
  padding: 12px 24px;
  font-size: 1rem;
  border-radius: 30px;
  cursor: pointer;
  box-shadow: 0 0 15px #ff8af0;
  transition: all 0.3s ease;
  margin-top: 20px;
}

button:hover {
  box-shadow: 0 0 25px #00e0ff, 0 0 35px #ff8af0;
  transform: scale(1.05);
}

.sparkle {
  position: absolute;
  width: 8px;
  height: 8px;
  background: white;
  border-radius: 50%;
  opacity: 0;
  box-shadow: 0 0 10px white;
  animation: twinkle 5s infinite;
}

@keyframes twinkle {
  0%, 100% {
    opacity: 0;
    transform: scale(0.5);
  }
  50% {
    opacity: 1;
    transform: scale(1.2);
  }
}
import React, { useEffect, useRef } from "react";

export default function App() {
  const audioRef = useRef(null);

  useEffect(() => {
    const audio = audioRef.current;
    if (audio) {
      const playPromise = audio.play();
      if (playPromise !== undefined) {
        playPromise.catch(() => {
          console.log("Autoplay blocked. User interaction needed.");
        });
      }
    }
  }, []);

  return (
    <div className="App">
      {[...Array(10)].map((_, i) => (
        <div
          className="sparkle"
          key={i}
          style={{
            top: `${Math.random() * 100}%`,
            left: `${Math.random() * 100}%`,
            animationDuration: `${2 + Math.random() * 3}s`,
            animationDelay: `${Math.random() * 5}s`,
          }}
        />
      ))}

      <h1>Neon Dream UI</h1>
      <p>Welcome to your flashy new interface.</p>
      <button>Click Me</button>

      {/* Background Audio */}
      <audio ref={audioRef} src="/ambient-loop.mp3" loop preload="auto" />

      {/* GitHub Footer Link */}
      <footer style={{ marginTop: "30px", fontSize: "0.8rem" }}>
        <a
          href="https://github.com/YOUR-USERNAME/YOUR-REPO"
          target="_blank"
          rel="noopener noreferrer"
          style={{ color: "#ffffff", textDecoration: "underline" }}
        >
          View Source on GitHub
        </a>
      </footer>
    </div>
  );
}
