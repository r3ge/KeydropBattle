const TARGETS = ['TOXIC', 'DIABLO', 'MILSPEC', 'SPARK', 'DAGGER', 'ENERGY', 'ICE BLAST', 'ROCKET RACCON', 'TECH', 'DAGGERS'];

(async () => {
  while (true) {
    const offset = (Math.random() + 1.2);
    await new Promise(r => setTimeout(r, 100));
    try {
      const caseNames = (([...document.querySelectorAll('p.max-w-full.px-1.overflow-hidden')]).splice(0, 3)).map(e => e.textContent);
      const casePrices = (([...document.querySelectorAll('div.flex.items-center.justify-center.rounded-tl-lg')]).splice(0, 3)).map(e => e.textContent);
      if (casePrices[caseNames.indexOf(caseNames.find(name => TARGETS.includes(name)))] === 'FREE' && caseNames.some(str => TARGETS.includes(str))) {
        const btns = [...document.querySelectorAll('a.button.ml-1.mr-5')];
        const btn = btns[caseNames.indexOf(caseNames.find(name => TARGETS.includes(name)))];
        btn.click();
        while (true) {
          const offset = (Math.random() + 1.2);
          await new Promise(r => setTimeout(r, (100 * offset)));
          try {
            const joinBtn = document.querySelector('button.mt-4.button-green-dimmed');
            if (joinBtn) {
              joinBtn.click();
              break;
            }
          } catch {null;}
        }
      }
    } catch {null;}
  }
})();
