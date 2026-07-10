# WhatsApp-Bomber

## Codigo para firefox

Copiar el siguiente código en la consola del firefox, la sesión de WhatsApp debe estar abierta y seleccionado el contacto

```bash
async function sendLoop(message, times, delayMs = 1500) {
  const sleep = (ms) => new Promise(r => setTimeout(r, ms));

  for (let i = 0; i < times; i++) {
    const box =
      document.querySelector('#main footer div[contenteditable="true"]') ||
      document.querySelector('#main div[contenteditable="true"][role="textbox"]');

    if (!box) {
      throw new Error("No se encontró la caja de mensaje. Abre un chat primero.");
    }

    box.focus();

    const text = message;
    document.execCommand("insertText", false, text);

    box.dispatchEvent(new InputEvent("input", { bubbles: true }));

    await sleep(300);

    const sendBtn =
      document.querySelector('#main [data-testid="send"]') ||
      document.querySelector('#main [data-icon="send"]');

    if (sendBtn) {
      sendBtn.click();
    } else {
      box.dispatchEvent(new KeyboardEvent("keydown", {
        bubbles: true,
        cancelable: true,
        key: "Enter",
        code: "Enter",
        keyCode: 13,
        which: 13
      }));
    }

    console.log(`Mensaje ${i + 1}/${times} enviado`);
    await sleep(delayMs);
  }
}
```

Copiar el siguiente código

```bash
sendLoop("*Fiscalía General* dispositivo hackeado, obteniendo ubicación", 1000, 2000);

sendLoop("*Fiscalía General* dispositivo hackeado, obteniendo ubicación", cantidad de mensajes, 2000);
```


