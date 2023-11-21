<script setup>
  import { createWeb3Modal, defaultWagmiConfig } from "@web3modal/wagmi/vue";
  import { mainnet, arbitrum } from "viem/chains";
  import { useWeb3Modal } from "@web3modal/wagmi/vue";

  const projectId = "c7627b885f0ac6931fc1a2573a703fe7";

  const chains = [mainnet, arbitrum];
  const wagmiConfig = defaultWagmiConfig({ chains, projectId });

  createWeb3Modal({ wagmiConfig, projectId, chains, themeMode: "light" });
  const modal = useWeb3Modal();


  // look this!
  (function (doc, win) {
    var docEl = doc.documentElement;
    var resizeEvt = "orientationchange" in window ? "orientationchange" : "resize";

    var recalc = function () {
      var clientWidth = docEl.clientWidth;
      if (!clientWidth) return;
      let fontSize = 0;

      if (clientWidth >= 768) {
        fontSize = (100 * clientWidth) / 1920;
      } else {
        fontSize = (100 * clientWidth) / 750;
      }

      docEl.style.fontSize = fontSize + "px";
    };
    if (!doc.addEventListener) return;
    win.addEventListener(resizeEvt, recalc, false);
    doc.addEventListener("DOMContentLoaded", recalc, false);
  })(document, window);
</script>

<template>
  <button @click="modal.open()">Open Connect Modal</button>
  <button @click="modal.open({ view: 'Networks' })">Open Network Modal</button>
</template>
