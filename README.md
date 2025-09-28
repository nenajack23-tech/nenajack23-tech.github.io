# nenajack23-tech.github.io.

mkdir aura_capacitor_template && cd aura_capacitor_template

# Init Node project
npm init -y
npm install @capacitor/core @capacitor/cli @capacitor/assets live-server --save-dev

# Make dirs
mkdir -p www/icons resources

# package.json overwrite
cat > package.json <<'EOF'
{ ... }   # <-- paste the JSON above here
EOF

# capacitor.config.ts
cat > capacitor.config.ts <<'EOF'
import { CapacitorConfig } from '@capacitor/cli';
const config: CapacitorConfig = {
  appId: 'com.aura.alchemy.calculator',
  appName: 'AuraCalc',
  webDir: 'www',
  bundledWebRuntime: false,
};
export default config;
EOF

# index.html (paste full calculator code here)
cat > www/index.html <<'EOF'
<!DOCTYPE html>
<!-- paste your calculator HTML here -->
EOF

# manifest
cat > www/manifest.webmanifest <<'EOF'
{ ... }   # paste JSON from above
EOF

# service worker
echo "self.addEventListener('install',()=>self.skipWaiting()); self.addEventListener('activate',e=>e.waitUntil(self.clients.claim()));" > www/service-worker.js
