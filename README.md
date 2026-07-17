# baileys-reseh

Library WhatsApp Web berbasis Baileys dengan perbaikan **USync device resolve** dan **assertSessions** — mendukung preflight target tanpa harus chat dulu.

Dipublish oleh [cikikomo](https://www.npmjs.com/~cikikomo).

## Install

```bash
npm install baileys-reseh
```

**Requirements:** Node.js 20+

## Usage

```js
import makeWASocket, {
  useMultiFileAuthState,
  fetchLatestWaWebVersion,
  DisconnectReason,
} from 'baileys-reseh';

const { state, saveCreds } = await useMultiFileAuthState('./session');
const { version } = await fetchLatestWaWebVersion();

const sock = makeWASocket({
  version,
  auth: state,
  printQRInTerminal: true,
});

sock.ev.on('creds.update', saveCreds);
sock.ev.on('connection.update', (update) => {
  if (update.connection === 'open') console.log('connected');
});
```

### API tambahan (rese)

- `sock.getUSyncDevices(jids, useCache, ignoreZeroDevices)`
- `sock.assertSessions(jids, force)`

## Repository

- GitHub: [aryoagung321-sudo](https://github.com/aryoagung321-sudo)

## Credits

- **cikikomo** — author, maintenance & publish

## License

MIT — see [LICENSE](./LICENSE).
