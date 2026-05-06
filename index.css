import React, { useMemo, useState } from "react";
import { motion, AnimatePresence } from "framer-motion";

export default function LoveGachaApp() {
  const cardList = [
    { id: "c1", rarity: "Common", title: "Lovey", message: "I still wonder how and when we started using lovey 😂." },
    { id: "c2", rarity: "Common", title: "Thingy", message: "The influence my husband has on me has got me using 'thingy' in every sentence hahaha 😂." },
    { id: "c3", rarity: "Common", title: "Valo Date", message: "I promiseeee I won't rageee naaa!." },
    { id: "c4", rarity: "Common", title: "Tiny Maykee", message: "Your tiny wife will always follow you around for cuddles and kisses hehehe 🌹." },
    { id: "c5", rarity: "Common", title: "Huggies!", message: "Are you tired my love? Come come me give you huggies heheheh 🤗🤗😊😊." },
    { id: "c6", rarity: "Common", title: "Kissy!", message: "Ugh! loveyyyyyy me need kisssyy pleaseee! 🥺🥺🥺." },
    { id: "e1", rarity: "Epic", title: "Gremlin Wife", message: "I love being your little gremlin wife, but do you love having a gremlin wife? You betterrr!! 😤😤." },
    { id: "e2", rarity: "Epic", title: "Duo Forever?", message: "Lovey I hope you'd still want me as your duo in every game, even though I rage a lot and competitive 🥺🥺." },
    { id: "e3", rarity: "Epic", title: "Crazy Ass Girl", message: "Yes! For youuuuu 😏😏😏." },
    { id: "l1", rarity: "Legendary", title: "I choose you!", message: "I chooosee youuu loveyy koo! And only you! Always! Forever! heheheh 😘😘🥰🥰❤️❤️." },
    { id: "l2", rarity: "Legendary", title: "Home", message: "You are my home! My shelter, My Love! Away but never apart." },
    { id: "m1", rarity: "Mythic", title: "Gabby Hubby", message: "My favorite lifetime will always be the one where I married you! You are the greatest husband a girl can have! I LOVE YOU LOVEY! 🥺🥺🥰🥰❤️❤️❤️😍😍." },
  ];

  const rarityStyle = {
    Common: { emoji: "🌹", text: "text-zinc-700", border: "border-gray-300", bg: "bg-gradient-to-br from-white to-zinc-100", shadow: "shadow-gray-200" },
    Epic: { emoji: "🌹", text: "text-violet-700", border: "border-purple-400", bg: "bg-gradient-to-br from-violet-100 to-purple-200", shadow: "shadow-purple-200" },
    Legendary: { emoji: "🌹", text: "text-amber-700", border: "border-yellow-400", bg: "bg-gradient-to-br from-yellow-100 to-amber-200", shadow: "shadow-yellow-200" },
    Mythic: { emoji: "🌹", text: "text-rose-700", border: "border-pink-400", bg: "bg-gradient-to-br from-pink-100 to-rose-200", shadow: "shadow-pink-200" },
  };

  const [lovePoints, setLovePoints] = useState(25);
  const [totalPulls, setTotalPulls] = useState(0);
  const [collection, setCollection] = useState([]);
  const [lastPulls, setLastPulls] = useState([]);
  const [pulling, setPulling] = useState(false);
  const [petAction, setPetAction] = useState("idle");
  const [floatingText, setFloatingText] = useState(null);
  const [showFinalCard, setShowFinalCard] = useState(false);
  const [selectedShowcaseCard, setSelectedShowcaseCard] = useState(null);

  const uniqueUnlocked = useMemo(() => [...new Set(collection.map((card) => card.id))], [collection]);
  const completed = uniqueUnlocked.length === cardList.length;

  function getCardsByRarity(rarity) {
    return cardList.filter((card) => card.rarity === rarity);
  }

  function randomFrom(list) {
    return list[Math.floor(Math.random() * list.length)];
  }

  function guaranteeCard(nextPullNumber) {
    if (nextPullNumber === 500) return randomFrom(getCardsByRarity("Mythic"));
    if (nextPullNumber === 400) return randomFrom(getCardsByRarity("Legendary"));
    if (nextPullNumber === 300) return randomFrom(getCardsByRarity("Legendary"));
    if (nextPullNumber === 200) return randomFrom(getCardsByRarity("Epic"));
    if (nextPullNumber === 150) return randomFrom(getCardsByRarity("Epic"));
    if (nextPullNumber === 100) return randomFrom(getCardsByRarity("Epic"));
    return null;
  }

  function normalRoll() {
    const roll = Math.random() * 100;
    if (roll < 1) return randomFrom(getCardsByRarity("Mythic"));
    if (roll < 6) return randomFrom(getCardsByRarity("Legendary"));
    if (roll < 22) return randomFrom(getCardsByRarity("Epic"));
    return randomFrom(getCardsByRarity("Common"));
  }

  function rollOnce(nextPullNumber) {
    return guaranteeCard(nextPullNumber) || normalRoll();
  }

  function pull(count) {
    if (pulling || lovePoints < count) return;
    setPulling(true);
    setLovePoints((points) => points - count);

    window.setTimeout(() => {
      const results = [];
      for (let i = 1; i <= count; i += 1) {
        results.push(rollOnce(totalPulls + i));
      }
      setTotalPulls((pulls) => pulls + count);
      setCollection((previous) => [...previous, ...results]);
      setLastPulls(results);
      setPulling(false);
    }, 900);
  }

  function earnPoints(action, points) {
    setLovePoints((current) => current + points);
    setPetAction(action);
    setFloatingText(`+${points} Love Points`);
    window.setTimeout(() => {
      setPetAction("idle");
      setFloatingText(null);
      setSelectedShowcaseCard(null);
    }, 900);
  }

  function resetPrototype() {
    setLovePoints(25);
    setTotalPulls(0);
    setCollection([]);
    setLastPulls([]);
    setPulling(false);
    setPetAction("idle");
    setFloatingText(null);
  }

  function isUnlocked(cardId) {
    return uniqueUnlocked.includes(cardId);
  }

  return (
    <main className="min-h-screen bg-gradient-to-br from-rose-100 via-pink-50 to-white p-4 md:p-6 text-gray-900">
      <section className="mx-auto max-w-7xl">
        <header className="text-center mb-6">
          <p className="text-xs uppercase tracking-[0.35em] text-rose-500 font-black mb-2">Maykee's Love Gacha</p>
          <h1 className="text-3xl md:text-5xl font-black">HAPPY 5TH MONTH Edition</h1>
          <p className="text-gray-600 mt-2">Collect all 12 cards to unlock the final message 🌹</p>
        </header>

        <div className="grid grid-cols-1 lg:grid-cols-2 gap-5">
          <section className="bg-white rounded-[2rem] border border-rose-100 shadow-xl p-5 md:p-6 min-h-[520px] flex flex-col">
            <div className="flex items-center justify-between gap-3 mb-5">
              <div>
                <h2 className="text-2xl font-black">Pull Area</h2>
                <p className="text-sm text-gray-500">Love Points: {lovePoints}</p>
              </div>
              <div className="text-right text-sm text-gray-500">
                <p>Total Pulls: {totalPulls}</p>
                <p>Keep pulling for surprises ✨</p>
              </div>
            </div>

            <div className="flex-1 rounded-[1.5rem] bg-gradient-to-b from-gray-950 to-gray-800 p-5 flex items-center justify-center overflow-hidden">
              <AnimatePresence mode="wait">
                {pulling ? (
                  <motion.div key="pulling" initial={{ scale: 0.8, opacity: 0 }} animate={{ scale: [0.9, 1.1, 1], opacity: 1, rotate: [0, -3, 3, 0] }} exit={{ scale: 0.8, opacity: 0 }} className="text-center text-white">
                    <div className="text-8xl mb-4">✨</div>
                    <p className="text-2xl font-black">Opening pack...</p>
                  </motion.div>
                ) : lastPulls.length === 0 ? (
                  <motion.div key="empty" initial={{ opacity: 0, y: 10 }} animate={{ opacity: 1, y: 0 }} className="text-center text-white">
                    <div className="text-8xl mb-4">🎴</div>
                    <p className="text-xl font-bold">Ready to pull?</p>
                    <p className="text-sm text-gray-300 mt-2">1 Love Point = 1 Pull</p>
                  </motion.div>
                ) : (
                  <motion.div key={collection.length} initial={{ opacity: 0, y: 20 }} animate={{ opacity: 1, y: 0 }} className="w-full">
                    <div className={`grid ${lastPulls.length === 1 ? "grid-cols-1" : "grid-cols-2 md:grid-cols-5"} gap-3`}>
                      {lastPulls.map((card, index) => {
                        const style = rarityStyle[card.rarity];
                        return (
                          <motion.article key={`${card.id}-${index}-${collection.length}`} initial={{ rotateY: 90, opacity: 0 }} animate={{ rotateY: 0, opacity: 1 }} transition={{ delay: index * 0.06 }} className={`rounded-2xl border-2 ${style.border} ${style.bg} p-4 text-center shadow-xl ${style.shadow}`}>
                            <p className="text-4xl mb-2">{style.emoji}</p>
                            <p className={`text-xs font-black uppercase tracking-widest ${style.text}`}>{card.rarity}</p>
                            <h3 className="font-black mt-2">{card.title}</h3>
                            {lastPulls.length === 1 && <p className="text-sm text-gray-600 mt-3">{card.message}</p>}
                          </motion.article>
                        );
                      })}
                    </div>
                  </motion.div>
                )}
              </AnimatePresence>
            </div>

            <div className="grid grid-cols-2 gap-3 mt-5">
              <button type="button" onClick={() => pull(1)} disabled={pulling || lovePoints < 1} className="rounded-2xl bg-gray-950 text-white font-black py-4 shadow-lg hover:scale-[1.02] active:scale-95 transition disabled:opacity-40">1x Pull</button>
              <button type="button" onClick={() => pull(10)} disabled={pulling || lovePoints < 10} className="rounded-2xl bg-rose-500 text-white font-black py-4 shadow-lg hover:scale-[1.02] active:scale-95 transition disabled:opacity-40">10x Pull</button>
            </div>
          </section>

          <section className="grid grid-rows-2 gap-5 min-h-[520px]">
            <div className="bg-white rounded-[2rem] border border-rose-100 shadow-xl p-5 md:p-6 relative overflow-hidden">
              <div className="flex items-center justify-between mb-4">
                <div>
                  <h2 className="text-2xl font-black">Earn Love Points</h2>
                  <p className="text-sm text-gray-500">Take care of tiny Maykee pet hehe</p>
                </div>
                <button type="button" onClick={resetPrototype} className="text-sm font-bold text-rose-500 hover:text-rose-700">Reset</button>
              </div>

              <div className="relative h-36 rounded-[1.5rem] bg-gradient-to-br from-pink-100 to-rose-50 border border-rose-100 flex items-center justify-center overflow-hidden">
                <AnimatePresence>
                  {floatingText && (
                    <motion.div initial={{ opacity: 0, y: 20 }} animate={{ opacity: 1, y: -35 }} exit={{ opacity: 0 }} className="absolute top-12 font-black text-rose-600">{floatingText}</motion.div>
                  )}
                </AnimatePresence>

                <motion.div animate={petAction === "kiss" ? { scale: [1, 1.25, 1], rotate: [0, -8, 8, 0] } : petAction === "feed" ? { y: [0, -8, 0], scale: [1, 1.08, 1] } : petAction === "hug" ? { scale: [1, 1.18, 0.95, 1] } : petAction === "snuggle" ? { rotate: [0, -5, 5, -3, 0], y: [0, 5, 0] } : { y: [0, -6, 0] }} transition={petAction === "idle" ? { repeat: Infinity, duration: 2 } : { duration: 0.7 }} className="text-center">
                  <div className="text-xs bg-white/80 rounded-full px-3 py-1 font-black text-rose-500 shadow mb-2">maykee</div>
                  <div className="text-7xl">🐰</div>
                </motion.div>
              </div>

              <div className="grid grid-cols-2 gap-3 mt-4">
                <button onClick={() => earnPoints("kiss", 50)} className="rounded-2xl bg-pink-500 text-white font-black py-3 hover:scale-[1.02] active:scale-95 transition">Kiss +50</button>
                <button onClick={() => earnPoints("feed", 20)} className="rounded-2xl bg-orange-400 text-white font-black py-3 hover:scale-[1.02] active:scale-95 transition">Feed +20</button>
                <button onClick={() => earnPoints("hug", 30)} className="rounded-2xl bg-purple-500 text-white font-black py-3 hover:scale-[1.02] active:scale-95 transition">Hug +30</button>
                <button onClick={() => earnPoints("snuggle", 15)} className="rounded-2xl bg-blue-400 text-white font-black py-3 hover:scale-[1.02] active:scale-95 transition">Snuggle +15</button>
              </div>
            </div>

            <div className="bg-white rounded-[2rem] border border-rose-100 shadow-xl p-5 md:p-6 overflow-hidden">
              <div className="flex items-start justify-between gap-4 mb-4">
                <div>
                  <h2 className="text-2xl font-black">Showcase Deck</h2>
                  <p className="text-sm text-gray-500">{uniqueUnlocked.length}/12 unique cards unlocked</p>
                </div>
                {completed && (
                  <div className="flex flex-col items-end gap-2">
                    <p className="text-sm font-black text-rose-600">You collected every rose from my garden 🌹</p>
                    <button type="button" onClick={() => setShowFinalCard(true)} className="rounded-xl bg-rose-500 text-white px-4 py-2 text-sm font-black hover:scale-105 active:scale-95 transition">Reveal Final Card</button>
                  </div>
                )}
              </div>

              <div className="grid grid-cols-3 md:grid-cols-6 gap-2">
                {cardList.map((card) => {
                  const unlocked = isUnlocked(card.id);
                  const style = rarityStyle[card.rarity];
                  return (
                    <button type="button" key={card.id} onClick={() => unlocked && setSelectedShowcaseCard(card)} disabled={!unlocked} className={`aspect-[3/4] rounded-xl border-2 p-2 flex flex-col items-center justify-center text-center transition ${unlocked ? `${style.bg} ${style.border} hover:scale-105 hover:shadow-lg cursor-pointer` : "bg-gray-100 border-gray-200 cursor-not-allowed opacity-70"}`}>
                      <div className="text-2xl mb-1">{unlocked ? style.emoji : "❔"}</div>
                      <p className={`text-[10px] font-black uppercase ${unlocked ? style.text : "text-gray-400"}`}>{unlocked ? card.rarity : "Locked"}</p>
                      <p className="text-xs font-black mt-1 line-clamp-2">{unlocked ? card.title : "???"}</p>
                    </button>
                  );
                })}
              </div>
            </div>
          </section>
        </div>

        <AnimatePresence>
          {selectedShowcaseCard && (() => {
            const style = rarityStyle[selectedShowcaseCard.rarity];
            return (
              <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} exit={{ opacity: 0 }} className="fixed inset-0 bg-black/60 backdrop-blur-sm flex items-center justify-center p-4 z-50">
                <motion.div initial={{ scale: 0.85, opacity: 0, y: 25 }} animate={{ scale: 1, opacity: 1, y: 0 }} exit={{ scale: 0.85, opacity: 0 }} transition={{ type: "spring", stiffness: 140 }} className={`w-full max-w-md rounded-[2rem] border-4 ${style.border} ${style.bg} shadow-2xl p-8 text-center`}>
                  <p className={`text-xs uppercase tracking-[0.35em] font-black mb-3 ${style.text}`}>{selectedShowcaseCard.rarity}</p>
                  <div className="text-8xl mb-5">{style.emoji}</div>
                  <h2 className="text-3xl font-black mb-5">{selectedShowcaseCard.title}</h2>
                  <p className="text-lg leading-relaxed text-gray-700">{selectedShowcaseCard.message}</p>
                  <button type="button" onClick={() => setSelectedShowcaseCard(null)} className="mt-8 rounded-2xl bg-gray-950 text-white px-8 py-3 font-black hover:scale-105 active:scale-95 transition">Close</button>
                </motion.div>
              </motion.div>
            );
          })()}

          {showFinalCard && (
            <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} exit={{ opacity: 0 }} className="fixed inset-0 bg-black/70 backdrop-blur-sm flex items-center justify-center p-4 z-50">
              <motion.div initial={{ scale: 0.8, opacity: 0, y: 30 }} animate={{ scale: 1, opacity: 1, y: 0 }} exit={{ scale: 0.8, opacity: 0 }} transition={{ type: "spring", stiffness: 120 }} className="relative w-full max-w-2xl rounded-[2.5rem] border-4 border-pink-300 bg-gradient-to-b from-pink-100 via-white to-rose-100 shadow-2xl overflow-hidden">
                <div className="absolute inset-0 opacity-20 pointer-events-none">
                  <div className="absolute top-8 left-8 text-6xl">✨</div>
                  <div className="absolute bottom-10 right-10 text-7xl">💖</div>
                  <div className="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 text-[12rem] opacity-10">💍</div>
                </div>

                <div className="relative p-8 md:p-12 text-center">
                  <p className="text-xs uppercase tracking-[0.4em] text-rose-500 font-black mb-3">Final Unlock</p>
                  <div className="text-8xl mb-5">☀️🌙</div>
                  <h2 className="text-4xl md:text-5xl font-black mb-6 bg-gradient-to-r from-rose-500 to-pink-500 bg-clip-text text-transparent">MY GABBY MANALO</h2>

                  <div className="space-y-5 text-lg md:text-xl leading-relaxed text-gray-700 max-w-xl mx-auto">
                    <p>Love like yours is absolutely rare. Idk what I did to get this luck to have pulled you in this RNG of life but I'm not complaining. You are the single most precious thing in my life right now and I never wanna lose you.</p>
                    <p>Thank you for always loving me. Loving me through every version of your wife. The soft and loving, The always rages, The emotional wife, The overthinker, The too much, The crazy, but most importantly, The one that's yours.</p>
                    <p>I LOVE YOU SO SO MUCH PO MY BIBING ASAWA! 😍❤️🥰😍❤️🥰😘❤️🥰😘🥰❤️😍 Please don't ever leave my side po! 🥺🥺🥺</p>
                    <p className="font-black text-rose-500">No matter how many lifetimes exist, I think I would still keep finding my way back to you.</p>
                  </div>

                  <div className="mt-8 text-sm text-gray-500 font-bold">— Love, Maykee 🌹</div>
                  <button type="button" onClick={() => setShowFinalCard(false)} className="mt-10 rounded-2xl bg-gray-950 text-white px-8 py-4 font-black hover:scale-105 active:scale-95 transition">Close</button>
                </div>
              </motion.div>
            </motion.div>
          )}
        </AnimatePresence>
      </section>
    </main>
  );
}
