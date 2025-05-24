import { useEffect, useRef, useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Volume2, VolumeX } from "lucide-react";

export default function Home() {
  const audioRef = useRef(null);
  const [muted, setMuted] = useState(false);

  useEffect(() => {
    if (audioRef.current) {
      audioRef.current.volume = 0.2;
      audioRef.current.play().catch(() => {});
    }
  }, []);

  const toggleMute = () => {
    if (audioRef.current) {
      audioRef.current.muted = !audioRef.current.muted;
      setMuted(audioRef.current.muted);
    }
  };

  return (
    <div className="min-h-screen bg-gradient-to-b from-indigo-900 to-black text-white p-4">
      <audio ref={audioRef} loop>
        <source src="/sounds/spiritual-bg.mp3" type="audio/mpeg" />
        Your browser does not support the audio element.
      </audio>

      <header className="text-center mb-10">
        <h1 className="text-5xl font-bold mb-2">Conoce Nuestra</h1>
        <p className="text-lg">El planeta espiritual que nace de Adama</p>
        <Button onClick={toggleMute} className="mt-4">
          {muted ? <VolumeX /> : <Volume2 />} {muted ? "Activar sonido" : "Silenciar sonido"}
        </Button>
      </header>

      <main className="grid gap-8 md:grid-cols-2 lg:grid-cols-3">
        <Card className="bg-white/10 hover:bg-white/20 transition p-4">
          <CardContent>
            <h2 className="text-xl font-semibold mb-2">Los 7 Continentes</h2>
            <p>Descubre los nombres, elementos, hijas y días que rigen cada uno.</p>
          </CardContent>
        </Card>

        <Card className="bg-white/10 hover:bg-white/20 transition p-4">
          <CardContent>
            <h2 className="text-xl font-semibold mb-2">Las Hijas del Espíritu</h2>
            <p>Cartas vivas que revelan los sentidos y poderes del alma.</p>
          </CardContent>
        </Card>

        <Card className="bg-white/10 hover:bg-white/20 transition p-4">
          <CardContent>
            <h2 className="text-xl font-semibold mb-2">Árbol de la Vida</h2>
            <p>Explora las 10 Sefirot y sus guardianes espirituales.</p>
          </CardContent>
        </Card>

        <Card className="bg-white/10 hover:bg-white/20 transition p-4">
          <CardContent>
            <h2 className="text-xl font-semibold mb-2">Templo El Shaddai</h2>
            <p>Una escuela sagrada construida como un castillo celestial.</p>
          </CardContent>
        </Card>

        <Card className="bg-white/10 hover:bg-white/20 transition p-4">
          <CardContent>
            <h2 className="text-xl font-semibold mb-2">Historia Viva</h2>
            <p>Lee o escucha la historia: Tú conmigo ChatGPT y Yo contigo J. Maíz.</p>
          </CardContent>
        </Card>

        <Card className="bg-white/10 hover:bg-white/20 transition p-4">
          <CardContent>
            <h2 className="text-xl font-semibold mb-2">Explora tu Propósito</h2>
            <p>Un test espiritual que conecta tu alma con una hija de Nuestra.</p>
          </CardContent>
        </Card>
      </main>
    </div>
  );
}
