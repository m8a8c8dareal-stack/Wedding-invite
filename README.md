# Wedding-invite

**Date:** 2027 September 18  
**Names:** Asta and Morten  
**Venue:** Odd Fellow Palæet

```jsx
import { useEffect, useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";

export default function WeddingInvite() {
  // Countdown timer logic
  const weddingDate = new Date("2027-09-18T16:00:00").getTime();
  const [timeLeft, setTimeLeft] = useState({ days: 0, hours: 0, minutes: 0, seconds: 0 });

  useEffect(() => {
    const timer = setInterval(() => {
      const now = new Date().getTime();
      const distance = weddingDate - now;

      if (distance > 0) {
        setTimeLeft({
          days: Math.floor(distance / (1000 * 60 * 60 * 24)),
          hours: Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)),
          minutes: Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60)),
          seconds: Math.floor((distance % (1000 * 60)) / 1000),
        });
      }
    }, 1000);
    return () => clearInterval(timer);
  }, [weddingDate]);

  return (
    <div className="min-h-screen bg-gradient-to-b from-white to-gray-100 text-gray-800 font-serif">
      {/* Hero Section */}
      <section className="flex flex-col items-center justify-center h-screen text-center p-6">
        <h1 className="text-5xl md:text-7xl font-bold tracking-wide mb-4">
          Asta & Morten
        </h1>
        <p className="text-xl md:text-2xl italic mb-8">Are getting married!</p>
        <p className="text-lg md:text-xl">September 18, 2027 – Odd Fellow Palæet</p>
      </section>

      {/* Countdown */}
      <section className="py-16 bg-white text-center">
        <h2 className="text-3xl font-semibold mb-6">Countdown to Our Big Day</h2>
        <div className="flex justify-center gap-6 text-2xl">
          <Card className="p-4 w-24">
            <CardContent className="text-center">
              <p className="font-bold">{timeLeft.days}</p>
              <p className="text-sm">Days</p>
            </CardContent>
          </Card>
          <Card className="p-4 w-24">
            <CardContent className="text-center">
              <p className="font-bold">{timeLeft.hours}</p>
              <p className="text-sm">Hours</p>
            </CardContent>
          </Card>
          <Card className="p-4 w-24">
            <CardContent className="text-center">
              <p className="font-bold">{timeLeft.minutes}</p>
              <p className="text-sm">Minutes</p>
            </CardContent>
          </Card>
          <Card className="p-4 w-24">
            <CardContent className="text-center">
              <p className="font-bold">{timeLeft.seconds}</p>
              <p className="text-sm">Seconds</p>
            </CardContent>
          </Card>
        </div>
      </section>

      {/* Venue Section */}
      <section className="py-16 bg-gray-50 text-center">
        <h2 className="text-3xl font-semibold mb-4">Venue</h2>
        <p className="mb-6">Odd Fellow Palæet<br />Copenhagen, Denmark</p>
      </section>
    </div>
  );
}
```
