import React, { useMemo, useState } from 'react';
import { Card, CardContent, CardHeader, CardTitle } from '@/components/ui/card';
import { Button } from '@/components/ui/button';
import { Input } from '@/components/ui/input';
import { Label } from '@/components/ui/label';
import { Switch } from '@/components/ui/switch';
import { Progress } from '@/components/ui/progress';
import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/components/ui/tabs';
import { Badge } from '@/components/ui/badge';
import { Alert, AlertDescription } from '@/components/ui/alert';
import { Separator } from '@/components/ui/separator';
import { Table, TableBody, TableCell, TableHead, TableHeader, TableRow } from '@/components/ui/table';
import { ScrollArea } from '@/components/ui/scroll-area';
import { CardDescription } from '@/components/ui/card';
import { Activity, Gauge, Waves, Droplets, AlertTriangle, Power, RotateCw, Settings2, Network, Cpu, Cable, Factory, ArrowRightLeft, ShieldAlert, ListTree, PanelTop, Database } from 'lucide-react';

const clamp = (v, min, max) => Math.max(min, Math.min(max, v));

const STATUS_CLASS = {
  run: 'bg-emerald-500',
  stop: 'bg-slate-400',
  trip: 'bg-red-500',
  open: 'bg-sky-500',
  close: 'bg-slate-400',
  fault: 'bg-amber-500',
};

function StatusLamp({ state = 'stop', label }) {
  return (
    <div className="flex items-center gap-2 text-xs">
      <span className={`inline-block h-3 w-3 rounded-full ${STATUS_CLASS[state] || 'bg-slate-300'} shadow`} />
      <span className="text-slate-600">{label}</span>
    </div>
  );
}

function AnalogCard({ title, value, unit, min = 0, max = 100, icon: Icon = Gauge, subtitle }) {
  const pct = ((value - min) / (max - min)) * 100;
  return (
    <Card className="rounded-2xl shadow-sm border-slate-200">
      <CardContent className="pt-6 space-y-3">
        <div className="flex items-center justify-between gap-3">
          <div className="flex items-center gap-2">
            <Icon className="h-4 w-4" />
            <div>
              <div className="text-sm font-medium">{title}</div>
              {subtitle ? <div className="text-xs text-slate-500">{subtitle}</div> : null}
            </div>
          </div>
          <div className="text-xl font-semibold whitespace-nowrap">{value.toFixed(1)} {unit}</div>
        </div>
        <Progress value={clamp(pct, 0, 100)} />
        <div className="flex justify-between text-xs text-slate-500">
          <span>{min} {unit}</span>
          <span>{max} {unit}</span>
        </div>
      </CardContent>
    </Card>
  );
}

function EquipmentFaceplate({ title, type, running, trip, onToggle, meta, ioBits }) {
  return (
    <Card className="rounded-2xl shadow-sm border-slate-200">
      <CardHeader className="pb-3">
        <div className="flex items-center justify-between gap-3">
          <div>
            <CardTitle className="text-base">{title}</CardTitle>
            <CardDescription>{type}</CardDescription>
          </div>
          <Badge variant={trip ? 'destructive' : running ? 'default' : 'secondary'}>
            {trip ? 'TRIPPED' : running ? 'RUNNING' : 'STOPPED'}
          </Badge>
        </div>
      </CardHeader>
      <CardContent className="space-y-4">
        <div className="grid grid-cols-2 gap-2 text-xs">
          <StatusLamp state={running && !trip ? 'run' : 'stop'} label="RUN FB" />
          <StatusLamp state={trip ? 'trip' : 'stop'} label="TRIP FB" />
          {ioBits?.do ? <div className="rounded-lg border p-2">DO: <span className="font-medium">{ioBits.do}</span></div> : <div />}
          {ioBits?.di ? <div className="rounded-lg border p-2">DI: <span className="font-medium">{ioBits.di}</span></div> : <div />}
        </div>
        {meta ? <div className="text-xs text-slate-600 rounded-xl bg-slate-50 border p-3">{meta}</div> : null}
        {onToggle ? (
          <div className="flex items-center justify-between">
            <Label>Command</Label>
            <Switch checked={running} onCheckedChange={onToggle} disabled={trip} />
          </div>
        ) : null}
      </CardContent>
    </Card>
  );
}

function ValveFaceplate({ valve, onToggle }) {
  const openState = valve.fault ? 'fault' : valve.open ? 'open' : 'close';
  return (
    <Card className="rounded-2xl shadow-sm border-slate-200">
      <CardHeader className="pb-2">
        <div className="flex items-center justify-between gap-2">
          <div>
            <CardTitle className="text-sm">{valve.name}</CardTitle>
            <CardDescription>{valve.service}</CardDescription>
          </div>
          <Badge variant={valve.fault ? 'destructive' : valve.open ? 'default' : 'secondary'}>
            {valve.fault ? 'FAULT' : valve.open ? 'OPEN' : 'CLOSED'}
          </Badge>
        </div>
      </CardHeader>
      <CardContent className="space-y-3">
        <div className="grid grid-cols-2 gap-2 text-xs">
          <StatusLamp state={openState} label="OPEN LS" />
          <StatusLamp state={!valve.open && !valve.fault ? 'close' : 'stop'} label="CLOSE LS" />
          <div className="rounded-lg border p-2">DO: <span className="font-medium">{valve.doOpen}/{valve.doClose}</span></div>
          <div className="rounded-lg border p-2">DI: <span className="font-medium">{valve.diOpen}/{valve.diClose}</span></div>
          <div className="rounded-lg border p-2 col-span-2">Fault/Mode DI: <span className="font-medium">{valve.diFault} / {valve.diRemote}</span></div>
        </div>
        <div className="flex items-center justify-between">
          <Label>Open / Close</Label>
          <Switch checked={valve.open} onCheckedChange={onToggle} disabled={valve.fault} />
        </div>
      </CardContent>
    </Card>
  );
}

function Pipe({ x1, y1, x2, y2, active = false, dashed = false }) {
  return <line x1={x1} y1={y1} x2={x2} y2={y2} stroke={active ? '#0ea5e9' : '#94a3b8'} strokeWidth="6" strokeDasharray={dashed ? '8 6' : '0'} strokeLinecap="round" />;
}

function Tank({ x, y, w, h, levelPct = 50, title, sub }) {
  return (
    <g>
      <rect x={x} y={y} width={w} height={h} rx="16" fill="#ffffff" stroke="#475569" strokeWidth="2" />
      <rect x={x + 6} y={y + h - (h - 12) * (levelPct / 100) - 6} width={w - 12} height={(h - 12) * (levelPct / 100)} rx="10" fill="#bae6fd" />
      <text x={x + w / 2} y={y - 10} textAnchor="middle" fontSize="13" fontWeight="600" fill="#0f172a">{title}</text>
      <text x={x + w / 2} y={y + h + 18} textAnchor="middle" fontSize="11" fill="#475569">{sub}</text>
    </g>
  );
}

function PumpSymbol({ x, y, title, running, trip }) {
  return (
    <g>
      <circle cx={x} cy={y} r="24" fill="#fff" stroke={trip ? '#dc2626' : running ? '#16a34a' : '#64748b'} strokeWidth="4" />
      <path d={`M ${x - 8} ${y + 8} Q ${x + 4} ${y - 18} ${x + 10} ${y + 4}`} fill="none" stroke="#334155" strokeWidth="3" />
      <text x={x} y={y + 46} textAnchor="middle" fontSize="11" fontWeight="600" fill="#0f172a">{title}</text>
    </g>
  );
}

function ValveSymbol({ x, y, title, open, fault }) {
  const color = fault ? '#f59e0b' : open ? '#0ea5e9' : '#64748b';
  return (
    <g>
      <polygon points={`${x - 16},${y} ${x},${y - 16} ${x + 16},${y} ${x},${y + 16}`} fill="#fff" stroke={color} strokeWidth="3" />
      <text x={x} y={y + 34} textAnchor="middle" fontSize="11" fontWeight="600" fill="#0f172a">{title}</text>
    </g>
  );
}

function PidLikeMimic({ intake, wtp }) {
  const intakeRunning = intake.pumps.filter((p) => p.running && !p.trip).length;
  const inletFlow = wtp.linkEnabled ? intakeRunning * intake.flowPerPump : 0;
  const cwPumpsRunning = wtp.clearWaterPumps.filter((p) => p.running && !p.trip).length;
  return (
    <Card className="rounded-2xl shadow-sm border-slate-200 overflow-hidden">
      <CardHeader>
        <CardTitle className="text-base flex items-center gap-2"><Factory className="h-4 w-4" /> Process Mimic / P&ID Style Overview</CardTitle>
        <CardDescription>Linked intake well and WTP process view with equipment state, analog values, and actuator status.</CardDescription>
      </CardHeader>
      <CardContent>
        <div className="overflow-x-auto">
          <svg viewBox="0 0 1280 520" className="min-w-[1100px] w-full rounded-2xl bg-slate-50 border">
            <Pipe x1={90} y1={260} x2={210} y2={260} active={intakeRunning > 0} />
            <Pipe x1={210} y1={260} x2={330} y2={260} active={intakeRunning > 0} />
            <Pipe x1={390} y1={260} x2={510} y2={260} active={inletFlow > 0} />
            <Pipe x1={570} y1={260} x2={710} y2={260} active={wtp.flashMixer.running} />
            <Pipe x1={770} y1={260} x2={930} y2={260} active={wtp.flashMixer.running} />
            <Pipe x1={930} y1={260} x2={1030} y2={260} active={cwPumpsRunning > 0} />
            <Pipe x1={1030} y1={260} x2={1180} y2={260} active={cwPumpsRunning > 0} />

            <Tank x={20} y={160} w={70} h={120} levelPct={intake.level * 10} title="Intake Well" sub={`${intake.level.toFixed(1)} m`} />
            <PumpSymbol x={160} y={260} title="RW P1" running={intake.pumps[0].running} trip={intake.pumps[0].trip} />
            <PumpSymbol x={250} y={260} title="RW P2" running={intake.pumps[1].running} trip={intake.pumps[1].trip} />
            <PumpSymbol x={340} y={260} title="RW P3" running={intake.pumps[2].running} trip={intake.pumps[2].trip} />

            <ValveSymbol x={450} y={260} title="EMF-101" open={wtp.linkEnabled} fault={!wtp.linkEnabled} />
            <Tank x={510} y={150} w={80} h={140} levelPct={55} title="Flash Mixer" sub={wtp.flashMixer.running ? 'RUN' : 'STOP'} />
            <Tank x={710} y={140} w={90} h={160} levelPct={65} title="Clarifier" sub={`PT ${wtp.filterPressure.toFixed(1)} bar`} />
            <Tank x={930} y={140} w={90} h={160} levelPct={wtp.clearWaterLevel * 12.5} title="Clear Water Sump" sub={`${wtp.clearWaterLevel.toFixed(1)} m`} />
            <PumpSymbol x={1080} y={220} title="CWP-1" running={wtp.clearWaterPumps[0].running} trip={wtp.clearWaterPumps[0].trip} />
            <PumpSymbol x={1080} y={290} title="CWP-2" running={wtp.clearWaterPumps[1].running} trip={wtp.clearWaterPumps[1].trip} />
            <PumpSymbol x={1080} y={360} title="CWP-3" running={wtp.clearWaterPumps[2].running} trip={wtp.clearWaterPumps[2].trip} />

            <text x="420" y="230" fontSize="11" fill="#0f172a">Raw Water Flow: {inletFlow.toFixed(1)} m³/h</text>
            <text x="508" y="330" fontSize="11" fill="#0f172a">AI: LT/FT/PT + DI/DO Mapping Active</text>
            <text x="900" y="330" fontSize="11" fill="#0f172a">To OHT / Distribution</text>

            <rect x="520" y="360" width="120" height="70" rx="12" fill="#fff" stroke="#94a3b8" />
            <text x="580" y="385" textAnchor="middle" fontSize="12" fontWeight="600">Chemical Dosing</text>
            <text x="580" y="405" textAnchor="middle" fontSize="11">Alum: {wtp.alumOutput}%</text>
            <text x="580" y="420" textAnchor="middle" fontSize="11">Lime: {wtp.limeOutput}%</text>

            <rect x="800" y="360" width="130" height="70" rx="12" fill="#fff" stroke="#94a3b8" />
            <text x="865" y="385" textAnchor="middle" fontSize="12" fontWeight="600">Redundant PLC</text>
            <text x="865" y="405" textAnchor="middle" fontSize="11">CPU-A / CPU-B</text>
            <text x="865" y="420" textAnchor="middle" fontSize="11">ET200MP + Marshalling</text>
          </svg>
        </div>
      </CardContent>
    </Card>
  );
}

function IoMappingTable({ rows, title }) {
  return (
    <Card className="rounded-2xl shadow-sm border-slate-200">
      <CardHeader>
        <CardTitle className="text-base flex items-center gap-2"><ListTree className="h-4 w-4" /> {title}</CardTitle>
      </CardHeader>
      <CardContent>
        <ScrollArea className="h-[420px] rounded-xl border">
          <Table>
            <TableHeader className="sticky top-0 bg-white z-10">
              <TableRow>
                <TableHead>Tag</TableHead>
                <TableHead>Description</TableHead>
                <TableHead>Type</TableHead>
                <TableHead>PLC Addr.</TableHead>
                <TableHead>Module</TableHead>
                <TableHead>Status</TableHead>
              </TableRow>
            </TableHeader>
            <TableBody>
              {rows.map((row) => (
                <TableRow key={row.tag}>
                  <TableCell className="font-medium">{row.tag}</TableCell>
                  <TableCell>{row.description}</TableCell>
                  <TableCell>{row.type}</TableCell>
                  <TableCell>{row.address}</TableCell>
                  <TableCell>{row.module}</TableCell>
                  <TableCell>
                    <Badge variant={row.status === 'TRIP' || row.status === 'FAULT' ? 'destructive' : row.status === 'ON' || row.status === 'RUN' || row.status === 'OPEN' ? 'default' : 'secondary'}>
                      {row.status}
                    </Badge>
                  </TableCell>
                </TableRow>
              ))}
            </TableBody>
          </Table>
        </ScrollArea>
      </CardContent>
    </Card>
  );
}

function CommunicationPanel({ intake, wtp }) {
  const online = wtp.linkEnabled;
  const rows = [
    { device: 'EMF-101', protocol: 'Modbus RTU', id: 1, baud: 9600, parity: 'Even', status: online ? 'ONLINE' : 'OFFLINE' },
    { device: 'EMF-102', protocol: 'Modbus RTU', id: 2, baud: 9600, parity: 'Even', status: online ? 'ONLINE' : 'OFFLINE' },
    { device: 'Temp Scanner', protocol: 'Modbus RTU', id: 3, baud: 9600, parity: 'Even', status: 'ONLINE' },
    { device: 'Intake PLC Link', protocol: 'Modbus TCP / Ethernet', id: '-', baud: '-', parity: '-', status: online ? 'ONLINE' : 'OFFLINE' },
  ];
  return (
    <Card className="rounded-2xl shadow-sm border-slate-200">
      <CardHeader>
        <CardTitle className="text-base flex items-center gap-2"><Network className="h-4 w-4" /> Communication / Device Mapping</CardTitle>
        <CardDescription>All communication details visible for presentation and engineering review.</CardDescription>
      </CardHeader>
      <CardContent>
        <Table>
          <TableHeader>
            <TableRow>
              <TableHead>Device</TableHead>
              <TableHead>Protocol</TableHead>
              <TableHead>Device ID</TableHead>
              <TableHead>Baud Rate</TableHead>
              <TableHead>Parity</TableHead>
              <TableHead>Status</TableHead>
            </TableRow>
          </TableHeader>
          <TableBody>
            {rows.map((r) => (
              <TableRow key={r.device}>
                <TableCell className="font-medium">{r.device}</TableCell>
                <TableCell>{r.protocol}</TableCell>
                <TableCell>{r.id}</TableCell>
                <TableCell>{r.baud}</TableCell>
                <TableCell>{r.parity}</TableCell>
                <TableCell><Badge variant={r.status === 'ONLINE' ? 'default' : 'destructive'}>{r.status}</Badge></TableCell>
              </TableRow>
            ))}
          </TableBody>
        </Table>
        <div className="mt-4 grid md:grid-cols-4 gap-3 text-sm">
          <div className="rounded-xl border p-3">Data Bits<br /><span className="font-semibold">8</span></div>
          <div className="rounded-xl border p-3">Stop Bits<br /><span className="font-semibold">1</span></div>
          <div className="rounded-xl border p-3">CPU<br /><span className="font-semibold">1513R A/B</span></div>
          <div className="rounded-xl border p-3">Remote I/O<br /><span className="font-semibold">ET200MP</span></div>
        </div>
      </CardContent>
    </Card>
  );
}

function SystemArchitecture() {
  return (
    <Card className="rounded-2xl shadow-sm border-slate-200">
      <CardHeader>
        <CardTitle className="text-base flex items-center gap-2"><Cpu className="h-4 w-4" /> Control System Architecture</CardTitle>
      </CardHeader>
      <CardContent>
        <div className="grid lg:grid-cols-4 gap-4 text-sm">
          <div className="rounded-2xl border p-4 bg-slate-50">
            <div className="font-semibold flex items-center gap-2"><PanelTop className="h-4 w-4" /> Intake Well PLC</div>
            <div className="mt-2 text-slate-600">Raw water pumps, level, pressure, EMF.</div>
          </div>
          <div className="rounded-2xl border p-4 bg-slate-50">
            <div className="font-semibold flex items-center gap-2"><ArrowRightLeft className="h-4 w-4" /> Fiber / Ethernet</div>
            <div className="mt-2 text-slate-600">Intake data transferred to WTP for central monitoring.</div>
          </div>
          <div className="rounded-2xl border p-4 bg-slate-50">
            <div className="font-semibold flex items-center gap-2"><Cpu className="h-4 w-4" /> WTP Redundant PLC</div>
            <div className="mt-2 text-slate-600">CPU-1513R A/B with ET200MP I/O and hardwired actuator marshalling.</div>
          </div>
          <div className="rounded-2xl border p-4 bg-slate-50">
            <div className="font-semibold flex items-center gap-2"><Database className="h-4 w-4" /> SCADA / HMI</div>
            <div className="mt-2 text-slate-600">Overview mimic, interlocks, alarms, trends and bit-wise status presentation.</div>
          </div>
        </div>
      </CardContent>
    </Card>
  );
}

function buildIoRows(intake, wtp) {
  const rows = [];
  intake.pumps.forEach((pump, i) => {
    rows.push({ tag: `${pump.name.replace(/ /g, '_')}_RUN`, description: `${pump.name} running feedback`, type: 'DI', address: `I0.${i * 2}`, module: 'DI-1', status: pump.running && !pump.trip ? 'RUN' : 'OFF' });
    rows.push({ tag: `${pump.name.replace(/ /g, '_')}_TRIP`, description: `${pump.name} trip feedback`, type: 'DI', address: `I0.${i * 2 + 1}`, module: 'DI-1', status: pump.trip ? 'TRIP' : 'OFF' });
    rows.push({ tag: `${pump.name.replace(/ /g, '_')}_START`, description: `${pump.name} start command`, type: 'DO', address: `Q0.${i}`, module: 'DO-1', status: pump.running && !pump.trip ? 'ON' : 'OFF' });
  });
  wtp.clearWaterPumps.forEach((pump, i) => {
    rows.push({ tag: `${pump.name}_RUN`, description: `${pump.name} run feedback`, type: 'DI', address: `I1.${i * 2}`, module: 'DI-2', status: pump.running && !pump.trip ? 'RUN' : 'OFF' });
    rows.push({ tag: `${pump.name}_TRIP`, description: `${pump.name} trip feedback`, type: 'DI', address: `I1.${i * 2 + 1}`, module: 'DI-2', status: pump.trip ? 'TRIP' : 'OFF' });
    rows.push({ tag: `${pump.name}_START`, description: `${pump.name} soft starter command`, type: 'DO', address: `Q1.${i}`, module: 'DO-2', status: pump.running && !pump.trip ? 'ON' : 'OFF' });
  });
  rows.push({ tag: 'FLASH_MIXER_RUN', description: 'Flash mixer running', type: 'DI', address: 'I2.0', module: 'DI-3', status: wtp.flashMixer.running && !wtp.flashMixer.trip ? 'RUN' : 'OFF' });
  rows.push({ tag: 'FLASH_MIXER_TRIP', description: 'Flash mixer trip', type: 'DI', address: 'I2.1', module: 'DI-3', status: wtp.flashMixer.trip ? 'TRIP' : 'OFF' });
  rows.push({ tag: 'FLASH_MIXER_START', description: 'Flash mixer start command', type: 'DO', address: 'Q2.0', module: 'DO-3', status: wtp.flashMixer.running && !wtp.flashMixer.trip ? 'ON' : 'OFF' });
  rows.push({ tag: 'AIR_BLOWER_RUN', description: 'Air blower running', type: 'DI', address: 'I2.2', module: 'DI-3', status: wtp.airBlower.running && !wtp.airBlower.trip ? 'RUN' : 'OFF' });
  rows.push({ tag: 'AIR_BLOWER_TRIP', description: 'Air blower trip', type: 'DI', address: 'I2.3', module: 'DI-3', status: wtp.airBlower.trip ? 'TRIP' : 'OFF' });
  rows.push({ tag: 'AIR_BLOWER_START', description: 'Air blower start command', type: 'DO', address: 'Q2.1', module: 'DO-3', status: wtp.airBlower.running && !wtp.airBlower.trip ? 'ON' : 'OFF' });
  rows.push({ tag: 'LT101_PV', description: 'Intake/WTP linked level transmitter', type: 'AI', address: 'IW64', module: 'AI-1', status: `${intake.level.toFixed(1)} m` });
  rows.push({ tag: 'FT101_PV', description: 'Raw water flow value', type: 'AI', address: 'IW66', module: 'AI-1', status: `${(intake.pumps.filter((p) => p.running && !p.trip).length * intake.flowPerPump).toFixed(1)} m³/h` });
  rows.push({ tag: 'PT101_PV', description: 'Filter pressure transmitter', type: 'AI', address: 'IW68', module: 'AI-1', status: `${wtp.filterPressure.toFixed(1)} bar` });
  rows.push({ tag: 'AO101_ALUM', description: 'Alum dosing analog output', type: 'AO', address: 'QW64', module: 'AO-1', status: `${wtp.alumOutput}%` });
  rows.push({ tag: 'AO102_LIME', description: 'Lime dosing analog output', type: 'AO', address: 'QW66', module: 'AO-1', status: `${wtp.limeOutput}%` });
  wtp.valves.forEach((valve, i) => {
    rows.push({ tag: `${valve.name}_OPEN_CMD`, description: `${valve.name} open command`, type: 'DO', address: valve.doOpen, module: 'DO-Valve', status: valve.open && !valve.fault ? 'ON' : 'OFF' });
    rows.push({ tag: `${valve.name}_CLOSE_CMD`, description: `${valve.name} close command`, type: 'DO', address: valve.doClose, module: 'DO-Valve', status: !valve.open && !valve.fault ? 'ON' : 'OFF' });
    rows.push({ tag: `${valve.name}_OPEN_LS`, description: `${valve.name} open limit switch`, type: 'DI', address: valve.diOpen, module: 'DI-Valve', status: valve.open && !valve.fault ? 'OPEN' : 'OFF' });
    rows.push({ tag: `${valve.name}_CLOSE_LS`, description: `${valve.name} close limit switch`, type: 'DI', address: valve.diClose, module: 'DI-Valve', status: !valve.open && !valve.fault ? 'CLOSE' : 'OFF' });
    rows.push({ tag: `${valve.name}_FAULT`, description: `${valve.name} fault feedback`, type: 'DI', address: valve.diFault, module: 'DI-Valve', status: valve.fault ? 'FAULT' : 'OFF' });
    rows.push({ tag: `${valve.name}_REMOTE`, description: `${valve.name} local/remote feedback`, type: 'DI', address: valve.diRemote, module: 'DI-Valve', status: 'REMOTE' });
  });
  return rows;
}

function buildValve(index, name, service, open = false) {
  return {
    name,
    service,
    open,
    fault: false,
    doOpen: `Q${3 + Math.floor(index / 4)}.${(index * 2) % 8}`,
    doClose: `Q${3 + Math.floor(index / 4)}.${(index * 2 + 1) % 8}`,
    diOpen: `I${4 + Math.floor(index / 2)}.${(index * 4) % 8}`,
    diClose: `I${4 + Math.floor(index / 2)}.${(index * 4 + 1) % 8}`,
    diFault: `I${4 + Math.floor(index / 2)}.${(index * 4 + 2) % 8}`,
    diRemote: `I${4 + Math.floor(index / 2)}.${(index * 4 + 3) % 8}`,
  };
}

export default function App() {
  const [intake, setIntake] = useState({
    level: 6.5,
    flowPerPump: 120,
    pumps: [
      { name: 'RW Pump P1', running: true, trip: false },
      { name: 'RW Pump P2', running: false, trip: false },
      { name: 'RW Pump P3', running: false, trip: false },
    ],
  });

  const [wtp, setWtp] = useState({
    linkEnabled: true,
    filterPressure: 2.8,
    clearWaterLevel: 4.2,
    autoDosing: true,
    alumOutput: 42,
    limeOutput: 28,
    clearWaterPumps: [
      { name: 'CWP-1', running: true, trip: false },
      { name: 'CWP-2', running: false, trip: false },
      { name: 'CWP-3', running: false, trip: false },
    ],
    flashMixer: { running: true, trip: false },
    airBlower: { running: true, trip: false },
    valves: [
      buildValve(0, 'ACT-80-01', 'Filter Inlet', true),
      buildValve(1, 'ACT-80-02', 'Backwash Line'),
      buildValve(2, 'ACT-100-01', 'Clarifier Inlet', true),
      buildValve(3, 'ACT-100-02', 'Sludge Drain'),
      buildValve(4, 'ACT-150-01', 'Clear Water Header', true),
      buildValve(5, 'ACT-150-02', 'Wash Water Outlet'),
      buildValve(6, 'ACT-200-01', 'Raw Water Main', true),
      buildValve(7, 'OPEN-CH-GATE', 'Open Channel Gate', true),
    ],
  });

  const ioRows = useMemo(() => buildIoRows(intake, wtp), [intake, wtp]);
  const summary = useMemo(() => {
    const intakeTrips = intake.pumps.filter((p) => p.trip).length;
    const wtpTrips = [...wtp.clearWaterPumps, wtp.flashMixer, wtp.airBlower].filter((x) => x.trip).length;
    const valveFaults = wtp.valves.filter((v) => v.fault).length;
    return { intakeTrips, wtpTrips, valveFaults, totalIo: ioRows.length };
  }, [intake, wtp, ioRows]);

  const resetAll = () => {
    setIntake((prev) => ({ ...prev, pumps: prev.pumps.map((p) => ({ ...p, trip: false })) }));
    setWtp((prev) => ({
      ...prev,
      clearWaterPumps: prev.clearWaterPumps.map((p) => ({ ...p, trip: false })),
      flashMixer: { ...prev.flashMixer, trip: false },
      airBlower: { ...prev.airBlower, trip: false },
      valves: prev.valves.map((v) => ({ ...v, fault: false })),
    }));
  };

  const intakeRunning = intake.pumps.filter((p) => p.running && !p.trip).length;
  const inletFlow = wtp.linkEnabled ? intakeRunning * intake.flowPerPump : 0;

  return (
    <div className="min-h-screen bg-gradient-to-b from-slate-100 to-slate-50 p-4 md:p-6">
      <div className="max-w-7xl mx-auto space-y-6">
        <div className="flex flex-col xl:flex-row xl:items-center xl:justify-between gap-4">
          <div>
            <h1 className="text-3xl font-bold tracking-tight">WTP + Intake Well Interactive Simulator</h1>
            <p className="text-slate-600 mt-1 max-w-4xl">Detailed React-based engineering HMI with P&ID-style visuals, bit-wise I/O mapping, actuator marshalling view, communication mapping, and linked intake-to-WTP process simulation for technical submission and presentation.</p>
          </div>
          <div className="flex gap-3 flex-wrap">
            <Badge className="px-3 py-2 rounded-xl"><ShieldAlert className="w-4 h-4 mr-2" /> Intake Trips: {summary.intakeTrips}</Badge>
            <Badge className="px-3 py-2 rounded-xl" variant="secondary"><Power className="w-4 h-4 mr-2" /> WTP Trips: {summary.wtpTrips}</Badge>
            <Badge className="px-3 py-2 rounded-xl" variant="outline"><Cable className="w-4 h-4 mr-2" /> IO Points Shown: {summary.totalIo}</Badge>
            <Button variant="outline" onClick={resetAll}><RotateCw className="w-4 h-4 mr-2" /> Reset Faults</Button>
          </div>
        </div>

        <Alert className="rounded-2xl border-slate-300">
          <Settings2 className="h-4 w-4" />
          <AlertDescription>
            This version expands the interface with P&ID-like process graphics, device feedback presentation, PLC bit mapping, actuator marshalling status, and communication details aligned with the WTP and Intake Well engineering discussion.
          </AlertDescription>
        </Alert>

        <div className="grid lg:grid-cols-4 gap-4">
          <AnalogCard title="Intake Level" subtitle="LT-101" value={intake.level} unit="m" min={0} max={10} icon={Waves} />
          <AnalogCard title="Incoming Raw Water Flow" subtitle="FT-101" value={inletFlow} unit="m³/h" min={0} max={450} icon={Droplets} />
          <AnalogCard title="Filter Pressure" subtitle="PT-101" value={wtp.filterPressure} unit="bar" min={0} max={10} icon={Gauge} />
          <Card className="rounded-2xl shadow-sm border-slate-200">
            <CardContent className="pt-6 space-y-3">
              <div className="text-sm font-medium">Redundant Control State</div>
              <div className="grid grid-cols-2 gap-2 text-xs">
                <StatusLamp state="run" label="CPU-A Healthy" />
                <StatusLamp state="run" label="CPU-B Standby" />
                <StatusLamp state={wtp.linkEnabled ? 'run' : 'trip'} label="Intake Link" />
                <StatusLamp state="run" label="ET200MP Online" />
              </div>
            </CardContent>
          </Card>
        </div>

        <PidLikeMimic intake={intake} wtp={wtp} />
        <SystemArchitecture />
        <CommunicationPanel intake={intake} wtp={wtp} />

        <Card className="rounded-2xl shadow-sm border-slate-200">
          <CardContent className="pt-6">
            <Tabs defaultValue="intake" className="space-y-6">
              <TabsList className="grid grid-cols-5 w-full max-w-4xl">
                <TabsTrigger value="intake">Intake</TabsTrigger>
                <TabsTrigger value="wtp">WTP</TabsTrigger>
                <TabsTrigger value="valves">Valves</TabsTrigger>
                <TabsTrigger value="iomap">I/O Map</TabsTrigger>
                <TabsTrigger value="engineering">Engineering</TabsTrigger>
              </TabsList>

              <Separator />

              <TabsContent value="intake" className="space-y-6">
                <div className="grid md:grid-cols-4 gap-4">
                  <AnalogCard title="Intake Sump Level" value={intake.level} unit="m" min={0} max={10} icon={Waves} />
                  <AnalogCard title="Header Flow" value={intakeRunning * intake.flowPerPump} unit="m³/h" min={0} max={450} icon={Droplets} />
                  <AnalogCard title="Header Pressure" value={intakeRunning > 0 ? 2.2 + intakeRunning * 1.3 : 0} unit="bar" min={0} max={8} icon={Gauge} />
                  <Card className="rounded-2xl shadow-sm border-slate-200">
                    <CardHeader className="pb-2"><CardTitle className="text-base">Simulation Inputs</CardTitle></CardHeader>
                    <CardContent className="space-y-3">
                      <div className="space-y-1">
                        <Label>Level (m)</Label>
                        <Input type="number" value={intake.level} onChange={(e) => setIntake((prev) => ({ ...prev, level: clamp(Number(e.target.value || 0), 0, 10) }))} />
                      </div>
                      <div className="space-y-1">
                        <Label>Flow / Pump (m³/h)</Label>
                        <Input type="number" value={intake.flowPerPump} onChange={(e) => setIntake((prev) => ({ ...prev, flowPerPump: clamp(Number(e.target.value || 0), 0, 250) }))} />
                      </div>
                    </CardContent>
                  </Card>
                </div>
                <div className="grid xl:grid-cols-3 gap-4">
                  {intake.pumps.map((pump, idx) => (
                    <EquipmentFaceplate
                      key={pump.name}
                      title={pump.name}
                      type="Raw Water Pump"
                      running={pump.running}
                      trip={pump.trip}
                      onToggle={(checked) => setIntake((prev) => ({ ...prev, pumps: prev.pumps.map((p, i) => (i === idx ? { ...p, running: checked } : p)) }))}
                      meta="Signals visible: START DO, RUN DI, TRIP DI. Linked to WTP by Ethernet / Modbus TCP."
                      ioBits={{ do: `Q0.${idx}`, di: `I0.${idx * 2}/I0.${idx * 2 + 1}` }}
                    />
                  ))}
                </div>
              </TabsContent>

              <TabsContent value="wtp" className="space-y-6">
                <div className="grid lg:grid-cols-3 gap-4">
                  {wtp.clearWaterPumps.map((pump, idx) => (
                    <EquipmentFaceplate
                      key={pump.name}
                      title={pump.name}
                      type="5.5 kW Pump with Soft Starter"
                      running={pump.running}
                      trip={pump.trip}
                      onToggle={(checked) => setWtp((prev) => ({ ...prev, clearWaterPumps: prev.clearWaterPumps.map((p, i) => (i === idx ? { ...p, running: checked } : p)) }))}
                      meta="Soft starter based feeder. Run, trip, and command signals included in I/O map."
                      ioBits={{ do: `Q1.${idx}`, di: `I1.${idx * 2}/I1.${idx * 2 + 1}` }}
                    />
                  ))}
                </div>
                <div className="grid lg:grid-cols-3 gap-4">
                  <EquipmentFaceplate
                    title="Flash Mixer"
                    type="0.75 kW Process Drive"
                    running={wtp.flashMixer.running}
                    trip={wtp.flashMixer.trip}
                    onToggle={(checked) => setWtp((prev) => ({ ...prev, flashMixer: { ...prev.flashMixer, running: checked } }))}
                    meta="Process permissive equipment used in water treatment sequence."
                    ioBits={{ do: 'Q2.0', di: 'I2.0/I2.1' }}
                  />
                  <EquipmentFaceplate
                    title="Air Blower"
                    type="6.0 kW Blower"
                    running={wtp.airBlower.running}
                    trip={wtp.airBlower.trip}
                    onToggle={(checked) => setWtp((prev) => ({ ...prev, airBlower: { ...prev.airBlower, running: checked } }))}
                    meta="Supports process operations and shown as dedicated drive with feedback bits."
                    ioBits={{ do: 'Q2.1', di: 'I2.2/I2.3' }}
                  />
                  <Card className="rounded-2xl shadow-sm border-slate-200">
                    <CardHeader>
                      <CardTitle className="text-base">Chemical Dosing / Analog Outputs</CardTitle>
                    </CardHeader>
                    <CardContent className="space-y-4">
                      <div className="flex items-center justify-between">
                        <Label>Auto Dosing</Label>
                        <Switch checked={wtp.autoDosing} onCheckedChange={(v) => setWtp((prev) => ({ ...prev, autoDosing: v }))} />
                      </div>
                      <div>
                        <Label>AO-101 Alum (%)</Label>
                        <Input type="number" value={wtp.alumOutput} onChange={(e) => setWtp((prev) => ({ ...prev, alumOutput: clamp(Number(e.target.value || 0), 0, 100) }))} />
                      </div>
                      <div>
                        <Label>AO-102 Lime (%)</Label>
                        <Input type="number" value={wtp.limeOutput} onChange={(e) => setWtp((prev) => ({ ...prev, limeOutput: clamp(Number(e.target.value || 0), 0, 100) }))} />
                      </div>
                      <div className="text-xs text-slate-600 rounded-xl border p-3">AO Mapping: QW64 and QW66. Process values are reflected in the I/O mapping table.</div>
                    </CardContent>
                  </Card>
                </div>
              </TabsContent>

              <TabsContent value="valves" className="space-y-6">
                <Card className="rounded-2xl shadow-sm border-slate-200">
                  <CardHeader>
                    <CardTitle className="text-base flex items-center gap-2"><Cable className="h-4 w-4" /> Actuator Marshalling and Hardwired Feedback</CardTitle>
                    <CardDescription>Each actuator shows OPEN/CLOSE command bits and OPEN/CLOSE/FAULT/REMOTE feedback bits.</CardDescription>
                  </CardHeader>
                  <CardContent>
                    <div className="grid md:grid-cols-2 xl:grid-cols-4 gap-4">
                      {wtp.valves.map((valve, idx) => (
                        <ValveFaceplate key={valve.name} valve={valve} onToggle={(checked) => setWtp((prev) => ({ ...prev, valves: prev.valves.map((v, i) => (i === idx ? { ...v, open: checked } : v)) }))} />
                      ))}
                    </div>
                  </CardContent>
                </Card>
              </TabsContent>

              <TabsContent value="iomap" className="space-y-6">
                <IoMappingTable rows={ioRows} title="Detailed PLC I/O Mapping with Live Status" />
              </TabsContent>

              <TabsContent value="engineering" className="space-y-6">
                <div className="grid lg:grid-cols-2 gap-4">
                  <Card className="rounded-2xl shadow-sm border-slate-200">
                    <CardHeader>
                      <CardTitle className="text-base">Engineering Basis</CardTitle>
                    </CardHeader>
                    <CardContent className="space-y-3 text-sm text-slate-700">
                      <div className="rounded-xl border p-3">WTP PLC: Siemens S7-1500R, CPU-1513R (Redundant A/B)</div>
                      <div className="rounded-xl border p-3">Remote I/O: ET200MP</div>
                      <div className="rounded-xl border p-3">All 33 actuators considered through marshalling arrangement with hardwired command and feedback philosophy.</div>
                      <div className="rounded-xl border p-3">5.5 kW clear water pumps shown with soft starter control philosophy.</div>
                    </CardContent>
                  </Card>
                  <Card className="rounded-2xl shadow-sm border-slate-200">
                    <CardHeader>
                      <CardTitle className="text-base">I/O Summary</CardTitle>
                    </CardHeader>
                    <CardContent>
                      <Table>
                        <TableBody>
                          <TableRow><TableCell>Digital Inputs</TableCell><TableCell className="font-semibold">180 Required / 192 Installed</TableCell></TableRow>
                          <TableRow><TableCell>Digital Outputs</TableCell><TableCell className="font-semibold">90 Required / 96 Installed</TableCell></TableRow>
                          <TableRow><TableCell>Analog Inputs</TableCell><TableCell className="font-semibold">7 Required / 16 Installed</TableCell></TableRow>
                          <TableRow><TableCell>Analog Outputs</TableCell><TableCell className="font-semibold">2 Required / 4 Installed</TableCell></TableRow>
                          <TableRow><TableCell>Communication</TableCell><TableCell className="font-semibold">EMF-101, EMF-102, Temp Scanner, Intake PLC Link</TableCell></TableRow>
                        </TableBody>
                      </Table>
                    </CardContent>
                  </Card>
                </div>
              </TabsContent>
            </Tabs>
          </CardContent>
        </Card>
      </div>
    </div>
  );
}
