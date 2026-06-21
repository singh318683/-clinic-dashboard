<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Riverside Family Clinic — Queue &amp; Scheduling</title>
<script src="https://cdn.tailwindcss.com"></script>
<script src="https://unpkg.com/react@18/umd/react.production.min.js" crossorigin></script>
<script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js" crossorigin></script>
</head>
<body>
<div id="root"></div>
<script>
const {
  useState
} = React;
const IconPulse = ({
  className
}) => /*#__PURE__*/React.createElement("svg", {
  className: className,
  viewBox: "0 0 24 24",
  fill: "none",
  stroke: "currentColor",
  strokeWidth: "2",
  strokeLinecap: "round",
  strokeLinejoin: "round"
}, /*#__PURE__*/React.createElement("path", {
  d: "M3 12h4l2 6 4-12 2 6h6"
}));
const IconClock = ({
  className
}) => /*#__PURE__*/React.createElement("svg", {
  className: className,
  viewBox: "0 0 24 24",
  fill: "none",
  stroke: "currentColor",
  strokeWidth: "1.8",
  strokeLinecap: "round",
  strokeLinejoin: "round"
}, /*#__PURE__*/React.createElement("circle", {
  cx: "12",
  cy: "12",
  r: "9"
}), /*#__PURE__*/React.createElement("path", {
  d: "M12 7v5l3.5 2"
}));
const IconCheckCircle = ({
  className
}) => /*#__PURE__*/React.createElement("svg", {
  className: className,
  viewBox: "0 0 24 24",
  fill: "none",
  stroke: "currentColor",
  strokeWidth: "1.8",
  strokeLinecap: "round",
  strokeLinejoin: "round"
}, /*#__PURE__*/React.createElement("circle", {
  cx: "12",
  cy: "12",
  r: "9"
}), /*#__PURE__*/React.createElement("path", {
  d: "M8.5 12.5l2.5 2.5 4.5-5.5"
}));
const IconXCircle = ({
  className
}) => /*#__PURE__*/React.createElement("svg", {
  className: className,
  viewBox: "0 0 24 24",
  fill: "none",
  stroke: "currentColor",
  strokeWidth: "1.8",
  strokeLinecap: "round",
  strokeLinejoin: "round"
}, /*#__PURE__*/React.createElement("circle", {
  cx: "12",
  cy: "12",
  r: "9"
}), /*#__PURE__*/React.createElement("path", {
  d: "M9.5 9.5l5 5M14.5 9.5l-5 5"
}));
const IconPlus = ({
  className
}) => /*#__PURE__*/React.createElement("svg", {
  className: className,
  viewBox: "0 0 24 24",
  fill: "none",
  stroke: "currentColor",
  strokeWidth: "2",
  strokeLinecap: "round"
}, /*#__PURE__*/React.createElement("path", {
  d: "M12 5v14M5 12h14"
}));
const IconSearch = ({
  className
}) => /*#__PURE__*/React.createElement("svg", {
  className: className,
  viewBox: "0 0 24 24",
  fill: "none",
  stroke: "currentColor",
  strokeWidth: "1.8",
  strokeLinecap: "round",
  strokeLinejoin: "round"
}, /*#__PURE__*/React.createElement("circle", {
  cx: "11",
  cy: "11",
  r: "6"
}), /*#__PURE__*/React.createElement("path", {
  d: "M20 20l-3.5-3.5"
}));
const IconX = ({
  className
}) => /*#__PURE__*/React.createElement("svg", {
  className: className,
  viewBox: "0 0 24 24",
  fill: "none",
  stroke: "currentColor",
  strokeWidth: "2",
  strokeLinecap: "round"
}, /*#__PURE__*/React.createElement("path", {
  d: "M6 6l12 12M18 6L6 18"
}));
const IconUserCheck = ({
  className
}) => /*#__PURE__*/React.createElement("svg", {
  className: className,
  viewBox: "0 0 24 24",
  fill: "none",
  stroke: "currentColor",
  strokeWidth: "1.8",
  strokeLinecap: "round",
  strokeLinejoin: "round"
}, /*#__PURE__*/React.createElement("circle", {
  cx: "9",
  cy: "8",
  r: "3.2"
}), /*#__PURE__*/React.createElement("path", {
  d: "M3.5 19a6 6 0 0 1 11 0"
}), /*#__PURE__*/React.createElement("path", {
  d: "M16.5 11.5l2 2 3.5-4"
}));
const IconChevronRight = ({
  className
}) => /*#__PURE__*/React.createElement("svg", {
  className: className,
  viewBox: "0 0 24 24",
  fill: "none",
  stroke: "currentColor",
  strokeWidth: "2",
  strokeLinecap: "round",
  strokeLinejoin: "round"
}, /*#__PURE__*/React.createElement("path", {
  d: "M9 6l6 6-6 6"
}));
const DOCTOR_COLORS = {
  teal: {
    solid: "bg-teal-700"
  },
  indigo: {
    solid: "bg-indigo-700"
  },
  purple: {
    solid: "bg-purple-700"
  }
};
const STATUS_STYLES = {
  scheduled: {
    label: "Scheduled",
    text: "text-slate-600",
    bg: "bg-slate-50",
    border: "border-slate-200"
  },
  waiting: {
    label: "Waiting",
    text: "text-amber-700",
    bg: "bg-amber-50",
    border: "border-amber-200"
  },
  "in-room": {
    label: "In room",
    text: "text-teal-700",
    bg: "bg-teal-50",
    border: "border-teal-200"
  },
  completed: {
    label: "Completed",
    text: "text-stone-400",
    bg: "bg-stone-50",
    border: "border-stone-200"
  },
  "no-show": {
    label: "No-show",
    text: "text-rose-600",
    bg: "bg-rose-50",
    border: "border-rose-200"
  }
};
const INITIAL_DOCTORS = [{
  id: "d1",
  name: "Dr. Sarah Chen",
  specialty: "Family medicine",
  color: "teal"
}, {
  id: "d2",
  name: "Dr. Marcus Patel",
  specialty: "Cardiology",
  color: "indigo"
}, {
  id: "d3",
  name: "Dr. Elena Torres",
  specialty: "Pediatrics",
  color: "purple"
}];
const ASSISTANTS = ["Jamie Reyes", "Olivia Brooks"];
const INITIAL_APPOINTMENTS = [{
  id: 1,
  ticket: 101,
  doctorId: "d1",
  time: "9:00 AM",
  patient: "Liam Brooks",
  age: 34,
  reason: "Annual physical",
  status: "completed"
}, {
  id: 2,
  ticket: 102,
  doctorId: "d1",
  time: "9:30 AM",
  patient: "Maria Gomez",
  age: 58,
  reason: "Hypertension follow-up",
  status: "completed"
}, {
  id: 3,
  ticket: 103,
  doctorId: "d1",
  time: "10:00 AM",
  patient: "David Okafor",
  age: 45,
  reason: "Persistent cough",
  status: "in-room"
}, {
  id: 4,
  ticket: 104,
  doctorId: "d1",
  time: "10:15 AM",
  patient: "Priya Nair",
  age: 29,
  reason: "Sprained ankle",
  status: "waiting"
}, {
  id: 5,
  ticket: 105,
  doctorId: "d1",
  time: "10:45 AM",
  patient: "Tom Bishop",
  age: 67,
  reason: "Diabetes check-in",
  status: "scheduled"
}, {
  id: 6,
  ticket: 106,
  doctorId: "d1",
  time: "11:15 AM",
  patient: "Hannah Lee",
  age: 22,
  reason: "Sore throat",
  status: "no-show"
}, {
  id: 7,
  ticket: 107,
  doctorId: "d2",
  time: "9:15 AM",
  patient: "Robert Kim",
  age: 61,
  reason: "Chest pain evaluation",
  status: "completed"
}, {
  id: 8,
  ticket: 108,
  doctorId: "d2",
  time: "9:45 AM",
  patient: "Susan Diaz",
  age: 70,
  reason: "ECG review",
  status: "waiting"
}, {
  id: 9,
  ticket: 109,
  doctorId: "d2",
  time: "10:30 AM",
  patient: "James Whitfield",
  age: 55,
  reason: "Post-stent follow-up",
  status: "scheduled"
}, {
  id: 10,
  ticket: 110,
  doctorId: "d2",
  time: "11:00 AM",
  patient: "Grace Liu",
  age: 48,
  reason: "Palpitations",
  status: "scheduled"
}, {
  id: 11,
  ticket: 111,
  doctorId: "d3",
  time: "9:00 AM",
  patient: "Noah Patel",
  age: 6,
  reason: "Wellness check",
  status: "completed"
}, {
  id: 12,
  ticket: 112,
  doctorId: "d3",
  time: "9:40 AM",
  patient: "Aria Thompson",
  age: 4,
  reason: "Ear infection",
  status: "in-room"
}, {
  id: 13,
  ticket: 113,
  doctorId: "d3",
  time: "10:10 AM",
  patient: "Ben Carter",
  age: 9,
  reason: "Asthma follow-up",
  status: "waiting"
}, {
  id: 14,
  ticket: 114,
  doctorId: "d3",
  time: "10:40 AM",
  patient: "Zoe Martinez",
  age: 2,
  reason: "Vaccination",
  status: "scheduled"
}];
const ORDER = {
  "in-room": 0,
  waiting: 1,
  scheduled: 2,
  completed: 3,
  "no-show": 4
};
const sortAppts = list => [...list].sort((a, b) => ORDER[a.status] - ORDER[b.status] || a.time.localeCompare(b.time));
function StatCard({
  label,
  value,
  Icon,
  accent
}) {
  return /*#__PURE__*/React.createElement("div", {
    className: "flex items-center gap-3 rounded-xl border border-stone-200 bg-white px-4 py-3"
  }, /*#__PURE__*/React.createElement("div", {
    className: `flex h-9 w-9 items-center justify-center rounded-lg ${accent}`
  }, /*#__PURE__*/React.createElement(Icon, {
    className: "h-4 w-4"
  })), /*#__PURE__*/React.createElement("div", null, /*#__PURE__*/React.createElement("p", {
    className: "text-xs text-stone-500"
  }, label), /*#__PURE__*/React.createElement("p", {
    className: "text-lg font-semibold text-stone-900"
  }, value)));
}
function StatusBadge({
  status
}) {
  const s = STATUS_STYLES[status];
  return /*#__PURE__*/React.createElement("span", {
    className: `inline-flex items-center rounded-full border px-2.5 py-0.5 text-xs font-medium ${s.text} ${s.bg} ${s.border}`
  }, s.label);
}
function Ticket({
  number
}) {
  return /*#__PURE__*/React.createElement("div", {
    className: "flex h-9 w-14 flex-none items-center justify-center rounded-md border border-dashed border-stone-300 bg-stone-50 font-mono text-xs text-stone-500"
  }, "#", number);
}
function AppointmentRow({
  appt,
  doctor,
  onCheckIn,
  onComplete,
  onNoShow,
  mode
}) {
  return /*#__PURE__*/React.createElement("div", {
    className: "flex items-center gap-3 rounded-xl border border-stone-200 bg-white px-3 py-2.5"
  }, /*#__PURE__*/React.createElement(Ticket, {
    number: appt.ticket
  }), /*#__PURE__*/React.createElement("div", {
    className: "w-16 flex-none text-sm text-stone-500"
  }, appt.time), /*#__PURE__*/React.createElement("div", {
    className: "min-w-0 flex-1"
  }, /*#__PURE__*/React.createElement("p", {
    className: "truncate text-sm font-medium text-stone-900"
  }, appt.patient, " ", /*#__PURE__*/React.createElement("span", {
    className: "font-normal text-stone-400"
  }, "· ", appt.age)), /*#__PURE__*/React.createElement("p", {
    className: "truncate text-xs text-stone-500"
  }, appt.reason, mode === "assistant" && doctor && /*#__PURE__*/React.createElement("span", null, " · ", doctor.name))), /*#__PURE__*/React.createElement(StatusBadge, {
    status: appt.status
  }), /*#__PURE__*/React.createElement("div", {
    className: "flex flex-none items-center gap-1.5"
  }, mode === "assistant" && appt.status === "scheduled" && /*#__PURE__*/React.createElement("button", {
    onClick: () => onCheckIn(appt.id),
    className: "rounded-md border border-stone-200 px-2.5 py-1 text-xs font-medium text-stone-600 hover:bg-stone-50"
  }, "Check in"), mode === "doctor" && appt.status === "in-room" && /*#__PURE__*/React.createElement("button", {
    onClick: () => onComplete(appt.id),
    className: "rounded-md border border-teal-200 bg-teal-50 px-2.5 py-1 text-xs font-medium text-teal-700 hover:bg-teal-100"
  }, "Mark complete"), (appt.status === "waiting" || appt.status === "scheduled") && /*#__PURE__*/React.createElement("button", {
    onClick: () => onNoShow(appt.id),
    className: "rounded-md px-2 py-1 text-xs text-stone-400 hover:text-rose-600"
  }, "No-show")));
}
function DoctorView({
  doctors,
  selectedDoctorId,
  setSelectedDoctorId,
  appointments,
  stats,
  onCallNext,
  onComplete,
  onNoShow
}) {
  return /*#__PURE__*/React.createElement("div", null, /*#__PURE__*/React.createElement("div", {
    className: "mb-5 flex flex-wrap gap-2"
  }, doctors.map(d => {
    const c = DOCTOR_COLORS[d.color];
    const active = d.id === selectedDoctorId;
    return /*#__PURE__*/React.createElement("button", {
      key: d.id,
      onClick: () => setSelectedDoctorId(d.id),
      className: `flex items-center gap-2 rounded-full border px-3 py-1.5 text-sm transition ${active ? `${c.solid} text-white border-transparent` : "bg-white text-stone-600 border-stone-200 hover:border-stone-300"}`
    }, /*#__PURE__*/React.createElement("span", {
      className: "font-medium"
    }, d.name), /*#__PURE__*/React.createElement("span", {
      className: active ? "text-white/80" : "text-stone-400"
    }, "· ", d.specialty));
  })), /*#__PURE__*/React.createElement("div", {
    className: "mb-5 grid grid-cols-3 gap-3 sm:max-w-md"
  }, /*#__PURE__*/React.createElement(StatCard, {
    label: "Waiting",
    value: stats.waiting,
    Icon: IconClock,
    accent: "bg-amber-50 text-amber-700"
  }), /*#__PURE__*/React.createElement(StatCard, {
    label: "In room",
    value: stats.inRoom,
    Icon: IconUserCheck,
    accent: "bg-teal-50 text-teal-700"
  }), /*#__PURE__*/React.createElement(StatCard, {
    label: "Completed",
    value: stats.completed,
    Icon: IconCheckCircle,
    accent: "bg-stone-100 text-stone-600"
  })), /*#__PURE__*/React.createElement("div", {
    className: "mb-4"
  }, /*#__PURE__*/React.createElement("button", {
    onClick: onCallNext,
    disabled: stats.inRoom > 0 || stats.waiting === 0,
    className: "inline-flex items-center gap-2 rounded-lg bg-teal-700 px-4 py-2 text-sm font-medium text-white transition hover:bg-teal-800 disabled:cursor-not-allowed disabled:bg-stone-200 disabled:text-stone-400"
  }, "Call next patient ", /*#__PURE__*/React.createElement(IconChevronRight, {
    className: "h-4 w-4"
  })), stats.inRoom > 0 && /*#__PURE__*/React.createElement("p", {
    className: "mt-1.5 text-xs text-stone-500"
  }, "Finish the current visit before calling the next patient.")), /*#__PURE__*/React.createElement("div", {
    className: "space-y-2"
  }, appointments.map(a => /*#__PURE__*/React.createElement(AppointmentRow, {
    key: a.id,
    appt: a,
    onComplete: onComplete,
    onNoShow: onNoShow,
    mode: "doctor"
  }))));
}
function AssistantView({
  doctors,
  appointments,
  filterDoctorId,
  setFilterDoctorId,
  query,
  setQuery,
  stats,
  onCheckIn,
  onComplete,
  onNoShow,
  onAdd
}) {
  return /*#__PURE__*/React.createElement("div", null, /*#__PURE__*/React.createElement("p", {
    className: "mb-4 text-sm text-stone-500"
  }, "Shared coverage today: ", ASSISTANTS.join(" & ")), /*#__PURE__*/React.createElement("div", {
    className: "mb-5 grid grid-cols-2 gap-3 sm:max-w-lg sm:grid-cols-4"
  }, /*#__PURE__*/React.createElement(StatCard, {
    label: "Waiting",
    value: stats.waiting,
    Icon: IconClock,
    accent: "bg-amber-50 text-amber-700"
  }), /*#__PURE__*/React.createElement(StatCard, {
    label: "In room",
    value: stats.inRoom,
    Icon: IconUserCheck,
    accent: "bg-teal-50 text-teal-700"
  }), /*#__PURE__*/React.createElement(StatCard, {
    label: "Completed",
    value: stats.completed,
    Icon: IconCheckCircle,
    accent: "bg-stone-100 text-stone-600"
  }), /*#__PURE__*/React.createElement(StatCard, {
    label: "No-shows",
    value: stats.noShow,
    Icon: IconXCircle,
    accent: "bg-rose-50 text-rose-600"
  })), /*#__PURE__*/React.createElement("div", {
    className: "mb-4 flex flex-wrap items-center gap-2"
  }, /*#__PURE__*/React.createElement("button", {
    onClick: () => setFilterDoctorId("all"),
    className: `rounded-full border px-3 py-1.5 text-sm transition ${filterDoctorId === "all" ? "bg-stone-900 text-white border-transparent" : "bg-white text-stone-600 border-stone-200"}`
  }, "All doctors"), doctors.map(d => {
    const c = DOCTOR_COLORS[d.color];
    const active = filterDoctorId === d.id;
    return /*#__PURE__*/React.createElement("button", {
      key: d.id,
      onClick: () => setFilterDoctorId(d.id),
      className: `rounded-full border px-3 py-1.5 text-sm transition ${active ? `${c.solid} text-white border-transparent` : "bg-white text-stone-600 border-stone-200"}`
    }, d.name);
  }), /*#__PURE__*/React.createElement("div", {
    className: "ml-auto flex items-center gap-2"
  }, /*#__PURE__*/React.createElement("div", {
    className: "relative"
  }, /*#__PURE__*/React.createElement(IconSearch, {
    className: "pointer-events-none absolute left-2.5 top-2.5 h-4 w-4 text-stone-400"
  }), /*#__PURE__*/React.createElement("input", {
    value: query,
    onChange: e => setQuery(e.target.value),
    placeholder: "Search patient",
    className: "rounded-lg border border-stone-200 bg-white py-2 pl-8 pr-3 text-sm outline-none focus:border-teal-400"
  })), /*#__PURE__*/React.createElement("button", {
    onClick: onAdd,
    className: "inline-flex items-center gap-1.5 rounded-lg bg-teal-700 px-3 py-2 text-sm font-medium text-white hover:bg-teal-800"
  }, /*#__PURE__*/React.createElement(IconPlus, {
    className: "h-4 w-4"
  }), " Add appointment"))), /*#__PURE__*/React.createElement("div", {
    className: "space-y-2"
  }, appointments.length === 0 && /*#__PURE__*/React.createElement("p", {
    className: "rounded-lg border border-dashed border-stone-200 py-8 text-center text-sm text-stone-400"
  }, "No appointments match."), appointments.map(a => /*#__PURE__*/React.createElement(AppointmentRow, {
    key: a.id,
    appt: a,
    doctor: doctors.find(d => d.id === a.doctorId),
    onCheckIn: onCheckIn,
    onComplete: onComplete,
    onNoShow: onNoShow,
    mode: "assistant"
  }))));
}
function AddAppointmentModal({
  doctors,
  onClose,
  onSave
}) {
  const [doctorId, setDoctorId] = useState(doctors[0].id);
  const [patient, setPatient] = useState("");
  const [age, setAge] = useState("");
  const [time, setTime] = useState("");
  const [reason, setReason] = useState("");
  const [walkIn, setWalkIn] = useState(true);
  const canSave = patient.trim() && time.trim() && reason.trim();
  return /*#__PURE__*/React.createElement("div", {
    className: "fixed inset-0 z-50 flex items-center justify-center bg-stone-900/40 p-4"
  }, /*#__PURE__*/React.createElement("div", {
    className: "w-full max-w-md rounded-2xl bg-white p-5 shadow-xl"
  }, /*#__PURE__*/React.createElement("div", {
    className: "mb-4 flex items-center justify-between"
  }, /*#__PURE__*/React.createElement("h2", {
    className: "text-base font-semibold text-stone-900"
  }, "Add appointment"), /*#__PURE__*/React.createElement("button", {
    onClick: onClose,
    className: "rounded-md p-1 text-stone-400 hover:bg-stone-100 hover:text-stone-600"
  }, /*#__PURE__*/React.createElement(IconX, {
    className: "h-4 w-4"
  }))), /*#__PURE__*/React.createElement("div", {
    className: "space-y-3"
  }, /*#__PURE__*/React.createElement("div", null, /*#__PURE__*/React.createElement("label", {
    className: "mb-1 block text-xs font-medium text-stone-500"
  }, "Doctor"), /*#__PURE__*/React.createElement("select", {
    value: doctorId,
    onChange: e => setDoctorId(e.target.value),
    className: "w-full rounded-lg border border-stone-200 px-3 py-2 text-sm outline-none focus:border-teal-400"
  }, doctors.map(d => /*#__PURE__*/React.createElement("option", {
    key: d.id,
    value: d.id
  }, d.name, " · ", d.specialty)))), /*#__PURE__*/React.createElement("div", {
    className: "grid grid-cols-2 gap-3"
  }, /*#__PURE__*/React.createElement("div", null, /*#__PURE__*/React.createElement("label", {
    className: "mb-1 block text-xs font-medium text-stone-500"
  }, "Patient name"), /*#__PURE__*/React.createElement("input", {
    value: patient,
    onChange: e => setPatient(e.target.value),
    className: "w-full rounded-lg border border-stone-200 px-3 py-2 text-sm outline-none focus:border-teal-400"
  })), /*#__PURE__*/React.createElement("div", null, /*#__PURE__*/React.createElement("label", {
    className: "mb-1 block text-xs font-medium text-stone-500"
  }, "Age"), /*#__PURE__*/React.createElement("input", {
    value: age,
    onChange: e => setAge(e.target.value),
    type: "number",
    min: "0",
    className: "w-full rounded-lg border border-stone-200 px-3 py-2 text-sm outline-none focus:border-teal-400"
  }))), /*#__PURE__*/React.createElement("div", {
    className: "grid grid-cols-2 gap-3"
  }, /*#__PURE__*/React.createElement("div", null, /*#__PURE__*/React.createElement("label", {
    className: "mb-1 block text-xs font-medium text-stone-500"
  }, "Time"), /*#__PURE__*/React.createElement("input", {
    value: time,
    onChange: e => setTime(e.target.value),
    placeholder: "e.g. 1:30 PM",
    className: "w-full rounded-lg border border-stone-200 px-3 py-2 text-sm outline-none focus:border-teal-400"
  })), /*#__PURE__*/React.createElement("div", {
    className: "flex items-end pb-2"
  }, /*#__PURE__*/React.createElement("label", {
    className: "flex items-center gap-2 text-sm text-stone-600"
  }, /*#__PURE__*/React.createElement("input", {
    type: "checkbox",
    checked: walkIn,
    onChange: e => setWalkIn(e.target.checked),
    className: "h-4 w-4 rounded border-stone-300"
  }), "Walk-in (arrived now)"))), /*#__PURE__*/React.createElement("div", null, /*#__PURE__*/React.createElement("label", {
    className: "mb-1 block text-xs font-medium text-stone-500"
  }, "Reason for visit"), /*#__PURE__*/React.createElement("input", {
    value: reason,
    onChange: e => setReason(e.target.value),
    className: "w-full rounded-lg border border-stone-200 px-3 py-2 text-sm outline-none focus:border-teal-400"
  }))), /*#__PURE__*/React.createElement("div", {
    className: "mt-5 flex justify-end gap-2"
  }, /*#__PURE__*/React.createElement("button", {
    onClick: onClose,
    className: "rounded-lg border border-stone-200 px-3 py-2 text-sm font-medium text-stone-600 hover:bg-stone-50"
  }, "Cancel"), /*#__PURE__*/React.createElement("button", {
    disabled: !canSave,
    onClick: () => onSave({
      doctorId,
      patient,
      age,
      time,
      reason,
      walkIn
    }),
    className: "rounded-lg bg-teal-700 px-3 py-2 text-sm font-medium text-white hover:bg-teal-800 disabled:cursor-not-allowed disabled:bg-stone-200 disabled:text-stone-400"
  }, "Save"))));
}
function ClinicDashboard() {
  const [role, setRole] = useState("doctor");
  const [doctors] = useState(INITIAL_DOCTORS);
  const [appointments, setAppointments] = useState(INITIAL_APPOINTMENTS);
  const [selectedDoctorId, setSelectedDoctorId] = useState(INITIAL_DOCTORS[0].id);
  const [filterDoctorId, setFilterDoctorId] = useState("all");
  const [query, setQuery] = useState("");
  const [showAddModal, setShowAddModal] = useState(false);
  const [nextTicket, setNextTicket] = useState(115);
  const callNext = doctorId => {
    setAppointments(prev => {
      const hasInRoom = prev.some(a => a.doctorId === doctorId && a.status === "in-room");
      if (hasInRoom) return prev;
      const idx = prev.findIndex(a => a.doctorId === doctorId && a.status === "waiting");
      if (idx === -1) return prev;
      const copy = [...prev];
      copy[idx] = {
        ...copy[idx],
        status: "in-room"
      };
      return copy;
    });
  };
  const updateStatus = (id, status) => {
    setAppointments(prev => prev.map(a => a.id === id ? {
      ...a,
      status
    } : a));
  };
  const addAppointment = ({
    doctorId,
    patient,
    age,
    time,
    reason,
    walkIn
  }) => {
    setAppointments(prev => [...prev, {
      id: Date.now(),
      ticket: nextTicket,
      doctorId,
      time,
      patient,
      age: age ? Number(age) : null,
      reason,
      status: walkIn ? "waiting" : "scheduled"
    }]);
    setNextTicket(n => n + 1);
    setShowAddModal(false);
  };
  const doctorAppointments = sortAppts(appointments.filter(a => a.doctorId === selectedDoctorId));
  const doctorStats = {
    waiting: doctorAppointments.filter(a => a.status === "waiting").length,
    inRoom: doctorAppointments.filter(a => a.status === "in-room").length,
    completed: doctorAppointments.filter(a => a.status === "completed").length
  };
  const filteredAll = appointments.filter(a => {
    const matchesDoctor = filterDoctorId === "all" || a.doctorId === filterDoctorId;
    const matchesQuery = a.patient.toLowerCase().includes(query.toLowerCase());
    return matchesDoctor && matchesQuery;
  });
  const clinicStats = {
    waiting: appointments.filter(a => a.status === "waiting").length,
    inRoom: appointments.filter(a => a.status === "in-room").length,
    completed: appointments.filter(a => a.status === "completed").length,
    noShow: appointments.filter(a => a.status === "no-show").length
  };
  return /*#__PURE__*/React.createElement("div", {
    className: "min-h-screen bg-stone-50 text-stone-900"
  }, /*#__PURE__*/React.createElement("div", {
    className: "mx-auto max-w-6xl px-4 py-6 sm:px-6"
  }, /*#__PURE__*/React.createElement("div", {
    className: "mb-6 flex flex-col gap-4 sm:flex-row sm:items-center sm:justify-between"
  }, /*#__PURE__*/React.createElement("div", {
    className: "flex items-center gap-3"
  }, /*#__PURE__*/React.createElement("div", {
    className: "flex h-10 w-10 items-center justify-center rounded-xl bg-teal-700"
  }, /*#__PURE__*/React.createElement(IconPulse, {
    className: "h-5 w-5 text-white"
  })), /*#__PURE__*/React.createElement("div", null, /*#__PURE__*/React.createElement("h1", {
    className: "text-lg font-semibold leading-tight text-stone-900"
  }, "Riverside Family Clinic"), /*#__PURE__*/React.createElement("p", {
    className: "text-xs text-stone-500"
  }, "Daily queue & scheduling"))), /*#__PURE__*/React.createElement("div", {
    className: "inline-flex rounded-lg border border-stone-200 bg-white p-1"
  }, /*#__PURE__*/React.createElement("button", {
    onClick: () => setRole("doctor"),
    className: `rounded-md px-3 py-1.5 text-sm font-medium transition ${role === "doctor" ? "bg-teal-700 text-white" : "text-stone-600 hover:bg-stone-50"}`
  }, "Doctor view"), /*#__PURE__*/React.createElement("button", {
    onClick: () => setRole("assistant"),
    className: `rounded-md px-3 py-1.5 text-sm font-medium transition ${role === "assistant" ? "bg-teal-700 text-white" : "text-stone-600 hover:bg-stone-50"}`
  }, "Assistant view"))), role === "doctor" ? /*#__PURE__*/React.createElement(DoctorView, {
    doctors: doctors,
    selectedDoctorId: selectedDoctorId,
    setSelectedDoctorId: setSelectedDoctorId,
    appointments: doctorAppointments,
    stats: doctorStats,
    onCallNext: () => callNext(selectedDoctorId),
    onComplete: id => updateStatus(id, "completed"),
    onNoShow: id => updateStatus(id, "no-show")
  }) : /*#__PURE__*/React.createElement(AssistantView, {
    doctors: doctors,
    appointments: sortAppts(filteredAll),
    filterDoctorId: filterDoctorId,
    setFilterDoctorId: setFilterDoctorId,
    query: query,
    setQuery: setQuery,
    stats: clinicStats,
    onCheckIn: id => updateStatus(id, "waiting"),
    onComplete: id => updateStatus(id, "completed"),
    onNoShow: id => updateStatus(id, "no-show"),
    onAdd: () => setShowAddModal(true)
  })), showAddModal && /*#__PURE__*/React.createElement(AddAppointmentModal, {
    doctors: doctors,
    onClose: () => setShowAddModal(false),
    onSave: addAppointment
  }));
}
ReactDOM.createRoot(document.getElementById("root")).render(/*#__PURE__*/React.createElement(ClinicDashboard, null));
</script>
</body>
</html>
