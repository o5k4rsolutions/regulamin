import React, { useState, useRef, useEffect } from 'react';
import { initializeApp, getApps } from 'firebase/app';
import { getAuth, signInAnonymously, onAuthStateChanged } from 'firebase/auth';
import { getFirestore, collection, addDoc, serverTimestamp } from 'firebase/firestore';
import { ChevronRight, CheckCircle, PenTool, Trash2, Save } from 'lucide-react';

// --- KONFIGURACJA FIREBASE TWOJEGO PROJEKTU ---
const firebaseConfig = {
  apiKey: "AIzaSyDmmID6nm3Y3f3w0gb2AB2vXm0S2L7NHsc",
  authDomain: "regulamin-6f74c.firebaseapp.com",
  projectId: "regulamin-6f74c",
  storageBucket: "regulamin-6f74c.firebasestorage.app",
  messagingSenderId: "829914362482",
  appId: "1:829914362482:web:54fc73f2aba61c3e4908eb",
  measurementId: "G-CDWXM5HQ2E"
};

// Inicjalizacja Firebase (zapobieganie wielokrotnej inicjalizacji)
const app = getApps().length === 0 ? initializeApp(firebaseConfig) : getApps()[0];
const auth = getAuth(app);
const db = getFirestore(app);
const appId = typeof __app_id !== 'undefined' ? __app_id : 'regulamin-6f74c-app';

export default function App() {
  const [step, setStep] = useState(1);
  const [user, setUser] = useState(null);
  const [isSaving, setIsSaving] = useState(false);
  const [saveStatus, setSaveStatus] = useState(null);
  
  const canvasRef = useRef(null);
  const [isDrawing, setIsDrawing] = useState(false);

  // Naprawiona logika autoryzacji - wymuszenie logowania anonimowego dla własnego projektu
  useEffect(() => {
    const initAuth = async () => {
      try {
        // Zignoruj __initial_auth_token jeśli powoduje mismatch i użyj logowania anonimowego
        await signInAnonymously(auth);
      } catch (err) {
        console.error("Auth error details:", err);
      }
    };
    
    initAuth();
    const unsubscribe = onAuthStateChanged(auth, (currentUser) => {
      setUser(currentUser);
    });
    return () => unsubscribe();
  }, []);

  // Obsługa rysowania na canvas
  const startDrawing = (e) => {
    const canvas = canvasRef.current;
    if (!canvas) return;
    const ctx = canvas.getContext('2d');
    const rect = canvas.getBoundingClientRect();
    const x = (e.clientX || (e.touches && e.touches[0].clientX)) - rect.left;
    const y = (e.clientY || (e.touches && e.touches[0].clientY)) - rect.top;

    ctx.beginPath();
    ctx.moveTo(x, y);
    setIsDrawing(true);
  };

  const draw = (e) => {
    if (!isDrawing) return;
    const canvas = canvasRef.current;
    const ctx = canvas.getContext('2d');
    const rect = canvas.getBoundingClientRect();
    const x = (e.clientX || (e.touches && e.touches[0].clientX)) - rect.left;
    const y = (e.clientY || (e.touches && e.touches[0].clientY)) - rect.top;

    ctx.lineTo(x, y);
    ctx.stroke();
    ctx.strokeStyle = '#000';
    ctx.lineWidth = 2;
    ctx.lineCap = 'round';
    
    if (e.touches) e.preventDefault();
  };

  const stopDrawing = () => {
    setIsDrawing(false);
  };

  const clearCanvas = () => {
    const canvas = canvasRef.current;
    if (!canvas) return;
    const ctx = canvas.getContext('2d');
    ctx.clearRect(0, 0, canvas.width, canvas.height);
  };

  // Zapis do Firestore
  const handleSaveSignature = async () => {
    if (!user) {
      setSaveStatus("Błąd: Czekam na autoryzację Firebase...");
      return;
    }

    setIsSaving(true);
    setSaveStatus(null);
    const canvas = canvasRef.current;
    const signatureData = canvas.toDataURL('image/png');

    try {
      // Ścieżka zgodna z RULE 1
      const signaturesCol = collection(db, 'artifacts', appId, 'public', 'data', 'signatures');
      
      await addDoc(signaturesCol, {
        userId: user.uid,
        signatureImage: signatureData,
        timestamp: serverTimestamp(),
        agreementDate: '2026-01-02',
        platform: 'EDURANGA',
        status: 'accepted'
      });

      setStep(3);
    } catch (error) {
      console.error("Firestore Save Error:", error);
      setSaveStatus("Błąd zapisu. Upewnij się, że Firestore ma włączone uprawnienia zapisu.");
    } finally {
      setIsSaving(false);
    }
  };

  return (
    <div className="min-h-screen bg-slate-50 flex items-center justify-center p-4 font-sans text-slate-900">
      <div className="max-w-2xl w-full bg-white rounded-2xl shadow-xl overflow-hidden border border-slate-200">
        
        {/* Header */}
        <div className="bg-blue-700 p-6 text-white text-center">
          <h1 className="text-2xl font-bold tracking-tight">WSiP • EDURANGA</h1>
          <p className="text-blue-100 text-sm mt-1">Regulamin i Umowa Konta Użytkownika</p>
        </div>

        {/* Progress Bar */}
        <div className="flex w-full h-1 bg-slate-100">
          <div className={`h-full transition-all duration-500 ${step >= 1 ? 'bg-blue-500 w-1/3' : 'w-0'}`}></div>
          <div className={`h-full transition-all duration-500 ${step >= 2 ? 'bg-blue-500 w-1/3' : 'w-0'}`}></div>
          <div className={`h-full transition-all duration-500 ${step >= 3 ? 'bg-blue-500 w-1/3' : 'w-0'}`}></div>
        </div>

        <div className="p-8">
          {step === 1 && (
            <div className="space-y-6">
              <div className="prose prose-slate max-h-96 overflow-y-auto pr-4 border-b border-slate-100 pb-4">
                <h2 className="text-lg font-bold mb-4">Regulamin Platformy</h2>
                <ol className="list-decimal space-y-3 pl-4 text-slate-700">
                  <li><strong>Zakaz udostępniania:</strong> Zakaz udostępniania konta i testów osobom trzecim...</li>
                  <li><strong>Bazy zadań:</strong> Nie wolno zapisywać baz zadań, jedynie testy.</li>
                  <li><strong>Hasło:</strong> Hasło będzie zmieniane co parę miesięcy.</li>
                  <li><strong>Dostęp:</strong> Konto może być w każdej chwili zabrane.</li>
                  <li><strong>Koszty:</strong> Posiadanie konta jest darmowe.</li>
                  <li><strong>Dane:</strong> Zakaz zmieniania danych i haseł.</li>
                  <li><strong>Relacje:</strong> Za wkurzanie administratora może zostać zmienione hasło.</li>
                  <li><strong>Publikacja:</strong> Całkowity zakaz publikowania loginu lub testów.</li>
                </ol>
                <p className="mt-6 text-xs text-slate-400 italic">
                  Regulamin z dnia 02.01.2026. Administrator może odebrać dostęp bez podania przyczyny.
                </p>
              </div>
              <button 
                onClick={() => setStep(2)}
                className="w-full bg-blue-600 hover:bg-blue-700 text-white font-bold py-4 px-6 rounded-xl flex items-center justify-center gap-2 transition-all transform hover:scale-[1.02]"
              >
                Przeczytałem i przechodzę do podpisu <ChevronRight size={20} />
              </button>
            </div>
          )}

          {step === 2 && (
            <div className="space-y-6">
              <div className="text-center">
                <PenTool className="mx-auto text-blue-600 mb-2" size={32} />
                <h2 className="text-xl font-bold">Podpis Elektroniczny</h2>
                <p className="text-slate-500 text-sm">Złóż podpis poniżej</p>
              </div>

              <div className="relative border-2 border-dashed border-slate-300 rounded-xl bg-slate-50">
                <canvas 
                  ref={canvasRef}
                  width={600}
                  height={250}
                  className="w-full h-64 touch-none cursor-crosshair"
                  onMouseDown={startDrawing}
                  onMouseMove={draw}
                  onMouseUp={stopDrawing}
                  onMouseOut={stopDrawing}
                  onTouchStart={startDrawing}
                  onTouchMove={draw}
                  onTouchEnd={stopDrawing}
                />
              </div>

              <div className="flex gap-4">
                <button onClick={clearCanvas} className="flex-1 border border-slate-300 py-3 px-4 rounded-xl flex items-center justify-center gap-2 hover:bg-slate-100 transition-colors">
                  <Trash2 size={18} /> Wyczyść
                </button>
                <button 
                  onClick={handleSaveSignature}
                  disabled={isSaving}
                  className="flex-[2] bg-green-600 hover:bg-green-700 disabled:bg-slate-400 text-white font-bold py-3 px-4 rounded-xl flex items-center justify-center gap-2 transition-all"
                >
                  {isSaving ? "Zapisywanie..." : <><Save size={18} /> Podpisz i Wyślij</>}
                </button>
              </div>
              {saveStatus && <p className="text-red-500 text-center text-sm">{saveStatus}</p>}
            </div>
          )}

          {step === 3 && (
            <div className="py-12 text-center space-y-4">
              <div className="bg-green-100 w-20 h-20 rounded-full flex items-center justify-center mx-auto mb-4">
                <CheckCircle className="text-green-600" size={48} />
              </div>
              <h2 className="text-2xl font-bold text-slate-800">Umowa podpisana!</h2>
              <p className="text-slate-600 max-w-sm mx-auto">Twój podpis został zapisany w projekcie: {firebaseConfig.projectId}</p>
            </div>
          )}
        </div>
      </div>
    </div>
  );
}
