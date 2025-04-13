"use client"

  

import { useState, useEffect } from "react"

import { motion } from "framer-motion"

import { Card, CardContent, CardHeader, CardTitle, CardDescription, CardFooter } from "@/components/ui/card"

import { Table, TableBody, TableCell, TableHead, TableHeader, TableRow } from "@/components/ui/table"

import { Badge } from "@/components/ui/badge"

import { Button } from "@/components/ui/button"

import { Input } from "@/components/ui/input"

import { CalendarIcon, CheckCircle2, XCircle, CreditCard, Search, Clock, AlertCircle } from "lucide-react"

import { useToast } from "@/components/ui/use-toast"

import { Tabs, TabsContent, TabsList, TabsTrigger } from "@/components/ui/tabs"

import { format, parseISO, addDays } from "date-fns"

import {

    Dialog,

    DialogContent,

    DialogDescription,

    DialogFooter,

    DialogHeader,

    DialogTitle,

} from "@/components/ui/dialog"

import { Calendar } from "@/components/ui/calendar"

import { Popover, PopoverContent, PopoverTrigger } from "@/components/ui/popover"

import { Select, SelectContent, SelectItem, SelectTrigger, SelectValue } from "@/components/ui/select"

import PaystackPop from "@paystack/inline-js"

  

// Define the valid variants for Badge

type BadgeVariant = "default" | "secondary" | "destructive" | "outline" | "success"

  

// Interface for Appointment

interface Appointment {

    id: number

    appointment_date: string

    appointment_time: string

    doctor_name: string

    department?: string

    status: "completed" | "scheduled" | "canceled"

    paid?: boolean

    amount?: number

}

  

// Dummy data for appointments with added department field

const dummyAppointments: Appointment[] = [

    {

        id: 1,

        appointment_date: "2023-10-26",

        appointment_time: "10:00 AM",

        doctor_name: "Dr. Smith",

        department: "Cardiology",

        status: "completed",

        paid: true,

        amount: 150,

    },

    {

        id: 2,

        appointment_date: "2023-11-15",

        appointment_time: "02:30 PM",

        doctor_name: "Dr. Jones",

        department: "Neurology",

        status: "scheduled",

        paid: false,

        amount: 200,

    },

    {

        id: 3,

        appointment_date: "2023-12-05",

        appointment_time: "11:00 AM",

        doctor_name: "Dr. Williams",

        department: "Orthopedics",

        status: "canceled",

        amount: 175,

    },

    {

        id: 4,

        appointment_date: "2023-12-15",

        appointment_time: "09:30 AM",

        doctor_name: "Dr. Johnson",

        department: "Pediatrics",

        status: "scheduled",

        paid: false,

        amount: 225,

    },

    {

        id: 5,

        appointment_date: "2023-12-18",

        appointment_time: "01:15 PM",

        doctor_name: "Dr. Garcia",

        department: "Dermatology",

        status: "scheduled",

        paid: true,

        amount: 180,

    },

]

  

// Available time slots

const timeSlots = [

    "09:00 AM",

    "09:30 AM",

    "10:00 AM",

    "10:30 AM",

    "11:00 AM",

    "11:30 AM",

    "12:00 PM",

    "12:30 PM",

    "01:00 PM",

    "01:30 PM",

    "02:00 PM",

    "02:30 PM",

    "03:00 PM",

    "03:30 PM",

    "04:00 PM",

    "04:30 PM",

    "05:00 PM",

]

  

// Status badge component with explicit types

const StatusBadge = ({ status }: { status: "completed" | "scheduled" | "canceled" }) => {

    let variant: BadgeVariant = "default"

    let icon = null

  

    switch (status) {

        case "completed":

            variant = "success"

            icon = <CheckCircle2 className="w-3.5 h-3.5 mr-1" />

            break

        case "scheduled":

            variant = "outline"

            icon = <Clock className="w-3.5 h-3.5 mr-1" />

            break

        case "canceled":

            variant = "destructive"

            icon = <XCircle className="w-3.5 h-3.5 mr-1" />

            break

    }

  

    return (

        <Badge variant={variant} className="flex items-center gap-1 font-medium">

            {icon}

            {status.charAt(0).toUpperCase() + status.slice(1)}

        </Badge>

    )

}

  

// Mobile appointment card component

const AppointmentCard = ({

                             appointment,

                             onPayment,

                             onReschedule,

                         }: {

    appointment: Appointment

    onPayment: (appointment: Appointment) => void

    onReschedule: (appointment: Appointment) => void

}) => {

    return (

        <Card className="mb-4">

            <CardHeader className="pb-2">

                <div className="flex justify-between items-start">

                    <div>

                        <CardTitle className="text-base">{appointment.doctor_name}</CardTitle>

                        <CardDescription>{appointment.department}</CardDescription>

                    </div>

                    <StatusBadge status={appointment.status} />

                </div>

            </CardHeader>

            <CardContent className="pb-2">

                <div className="grid grid-cols-2 gap-2 text-sm">

                    <div className="text-muted-foreground">Date:</div>

                    <div className="font-medium">{format(parseISO(appointment.appointment_date), "MMM dd, yyyy")}</div>

  

                    <div className="text-muted-foreground">Time:</div>

                    <div className="font-medium">{appointment.appointment_time}</div>

  

                    <div className="text-muted-foreground">Amount:</div>

                    <div className="font-medium">¢{appointment.amount?.toFixed(2)}</div>

                </div>

            </CardContent>

            <CardFooter className="pt-2">

                {appointment.status === "scheduled" && !appointment.paid ? (

                    <Button

                        onClick={() => onPayment(appointment)}

                        size="sm"

                        className="w-full bg-green-600 hover:bg-green-700 text-white flex items-center justify-center gap-1"

                    >

                        <CreditCard className="w-4 h-4" /> Pay Now

                    </Button>

                ) : appointment.status === "scheduled" && appointment.paid ? (

                    <Badge variant="success" className="w-full flex justify-center py-1">

                        <CheckCircle2 className="w-3.5 h-3.5 mr-1" /> Paid

                    </Badge>

                ) : appointment.status === "canceled" ? (

                    <Button

                        variant="outline"

                        size="sm"

                        className="w-full flex items-center justify-center gap-1"

                        onClick={() => onReschedule(appointment)}

                    >

                        <CalendarIcon className="w-4 h-4" /> Reschedule

                    </Button>

                ) : (

                    <Badge variant="outline" className="w-full flex justify-center py-1">

                        Completed

                    </Badge>

                )}

            </CardFooter>

        </Card>

    )

}

  

export default function AppointmentHistoryPage() {

    const [appointments, setAppointments] = useState<Appointment[]>([])

    const [filteredAppointments, setFilteredAppointments] = useState<Appointment[]>([])

    const [searchQuery, setSearchQuery] = useState("")

    const [statusFilter, setStatusFilter] = useState("all")

    const [isRescheduleOpen, setIsRescheduleOpen] = useState(false)

    const [selectedAppointment, setSelectedAppointment] = useState<Appointment | null>(null)

    const [rescheduleDate, setRescheduleDate] = useState<Date | undefined>(undefined)

    const [rescheduleTime, setRescheduleTime] = useState<string>("")

    const { toast } = useToast()

  

    useEffect(() => {

        // Simulate API fetch with a small delay

        const timer = setTimeout(() => {

            setAppointments(dummyAppointments)

            setFilteredAppointments(dummyAppointments)

        }, 500)

  

        return () => clearTimeout(timer)

    }, [])

  

    useEffect(() => {

        let result = [...appointments]

  

        // Apply status filter

        if (statusFilter !== "all") {

            result = result.filter((app) => app.status === statusFilter)

        }

  

        // Apply search filter

        if (searchQuery) {

            const query = searchQuery.toLowerCase()

            result = result.filter(

                (app) =>

                    app.doctor_name.toLowerCase().includes(query) ||

                    (app.department && app.department.toLowerCase().includes(query)),

            )

        }

  

        setFilteredAppointments(result)

    }, [statusFilter, searchQuery, appointments])

  

    const handlePayment = (appointment: Appointment) => {

        try {

            const paystack = new PaystackPop()

            paystack.newTransaction({

                key: process.env.NEXT_PUBLIC_PAYSTACK_PUBLIC_KEY as string,

                amount: (appointment.amount || 0) * 100,

                email: "patient@example.com",

                reference: `appointment-${appointment.id}-${Date.now()}`,

                onSuccess: (transaction) => {

                    toast({

                        title: "Payment Successful",

                        description: `Payment of ¢${appointment.amount} was successful!`,

                        variant: "success",

                    })

  

                    setAppointments((prevAppointments) =>

                        prevAppointments.map((app) => (app.id === appointment.id ? { ...app, paid: true } : app)),

                    )

                },

                onCancel: () => {

                    toast({

                        title: "Payment Canceled",

                        description: "Your payment was canceled.",

                        variant: "destructive",

                    })

                },

            })

        } catch (error) {

            console.error("Paystack error:", error)

            toast({

                title: "Payment Error",

                description: "There was an error processing your payment. Please try again.",

                variant: "destructive",

            })

        }

    }

  

    const handleRescheduleClick = (appointment: Appointment) => {

        setSelectedAppointment(appointment)

        setRescheduleDate(undefined)

        setRescheduleTime("")

        setIsRescheduleOpen(true)

    }

  

    const handleRescheduleSubmit = () => {

        if (!selectedAppointment || !rescheduleDate || !rescheduleTime) {

            toast({

                title: "Missing Information",

                description: "Please select both a date and time for your appointment.",

                variant: "destructive",

            })

            return

        }

  

        // Format the date to ISO string (YYYY-MM-DD)

        const formattedDate = format(rescheduleDate, "yyyy-MM-dd")

  

        // Update the appointment in the state

        const updatedAppointments = appointments.map((app) =>

            app.id === selectedAppointment.id

                ? {

                    ...app,

                    status: "scheduled",

                    appointment_date: formattedDate,

                    appointment_time: rescheduleTime,

                    paid: false,

                }

                : app,

        )

  

        setAppointments(updatedAppointments)

  

        toast({

            title: "Appointment Rescheduled",

            description: `Your appointment has been rescheduled to ${format(rescheduleDate, "MMMM d, yyyy")} at ${rescheduleTime}.`,

            variant: "success",

        })

  

        setIsRescheduleOpen(false)

    }

  

    const formatDate = (dateString: string) => {

        try {

            return format(parseISO(dateString), "MMM dd, yyyy")

        } catch (e) {

            return dateString

        }

    }

  

    return (

        <div className="container mx-auto px-4 py-8 max-w-7xl">

            <motion.div

                className="mb-8"

                initial={{ opacity: 0, y: -20 }}

                animate={{ opacity: 1, y: 0 }}

                transition={{ duration: 0.5 }}

            >

                <div className="text-center">

                <h1 className="text-3xl font-bold text-primary mb-2">Appointment History</h1>

                <p className="text-muted-foreground">Track and manage your medical appointments at Central Hospital</p>

                </div>

            </motion.div>

  

            <motion.div

                initial={{ opacity: 0, y: 20 }}

                animate={{ opacity: 1, y: 0 }}

                transition={{ duration: 0.5, delay: 0.2 }}

            >

                <Card className="shadow-sm border-muted">

                    <CardHeader className="pb-0">

                        <CardTitle className="text-xl text-primary flex items-center gap-2">

                            <CalendarIcon className="h-5 w-5" />

                            Your Appointments

                        </CardTitle>

                        <CardDescription>View and manage all your scheduled, completed, and canceled appointments</CardDescription>

                    </CardHeader>

  

                    <CardContent>

                        <Tabs defaultValue="all" value={statusFilter} onValueChange={setStatusFilter} className="mt-4">

                            <div className="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4 mb-6">

                                <TabsList className="mb-2 sm:mb-0 w-full sm:w-auto">

                                    <TabsTrigger value="all">All</TabsTrigger>

                                    <TabsTrigger value="scheduled">Scheduled</TabsTrigger>

                                    <TabsTrigger value="completed">Completed</TabsTrigger>

                                    <TabsTrigger value="canceled">Canceled</TabsTrigger>

                                </TabsList>

  

                                <div className="relative w-full sm:w-auto">

                                    <Search className="absolute left-2.5 top-2.5 h-4 w-4 text-muted-foreground" />

                                    <Input

                                        placeholder="Search doctor or department..."

                                        className="pl-9 w-full sm:w-[250px]"

                                        value={searchQuery}

                                        onChange={(e) => setSearchQuery(e.target.value)}

                                    />

                                </div>

                            </div>

  

                            {/* Content for all tabs */}

                            {["all", "scheduled", "completed", "canceled"].map((tabValue) => (

                                <TabsContent key={tabValue} value={tabValue} className="m-0">

                                    {filteredAppointments.length > 0 ? (

                                        <>

                                            {/* Desktop view - Table */}

                                            <div className="hidden md:block rounded-md border overflow-hidden">

                                                <Table>

                                                    <TableHeader className="bg-muted/30">

                                                        <TableRow>

                                                            <TableHead className="font-semibold">Date & Time</TableHead>

                                                            <TableHead className="font-semibold">Doctor</TableHead>

                                                            <TableHead className="font-semibold">Department</TableHead>

                                                            <TableHead className="font-semibold">Status</TableHead>

                                                            <TableHead className="font-semibold text-right">Amount</TableHead>

                                                            <TableHead className="font-semibold text-right">Action</TableHead>

                                                        </TableRow>

                                                    </TableHeader>

                                                    <TableBody>

                                                        {filteredAppointments.map((appointment, index) => (

                                                            <motion.tr

                                                                key={appointment.id}

                                                                initial={{ opacity: 0, y: 10 }}

                                                                animate={{ opacity: 1, y: 0 }}

                                                                transition={{ duration: 0.3, delay: index * 0.05 }}

                                                                className={index % 2 === 0 ? "bg-muted/10" : ""}

                                                            >

                                                                <TableCell>

                                                                    <div className="flex flex-col">

                                    <span className="font-medium text-primary">

                                      {formatDate(appointment.appointment_date)}

                                    </span>

                                                                        <span className="text-sm text-muted-foreground flex items-center gap-1">

                                      <Clock className="h-3 w-3" /> {appointment.appointment_time}

                                    </span>

                                                                    </div>

                                                                </TableCell>

                                                                <TableCell className="font-medium">{appointment.doctor_name}</TableCell>

                                                                <TableCell className="text-muted-foreground">{appointment.department}</TableCell>

                                                                <TableCell>

                                                                    <StatusBadge status={appointment.status} />

                                                                </TableCell>

                                                                <TableCell className="font-medium text-right">

                                                                    ¢{appointment.amount?.toFixed(2)}

                                                                </TableCell>

                                                                <TableCell className="text-right">

                                                                    {appointment.status === "scheduled" && !appointment.paid ? (

                                                                        <Button

                                                                            onClick={() => handlePayment(appointment)}

                                                                            size="sm"

                                                                            className="bg-green-600 hover:bg-green-700 text-white flex items-center gap-1"

                                                                        >

                                                                            <CreditCard className="w-4 h-4" /> Pay Now

                                                                        </Button>

                                                                    ) : appointment.status === "scheduled" && appointment.paid ? (

                                                                        <Badge variant="success" className="ml-auto">

                                                                            <CheckCircle2 className="w-3.5 h-3.5 mr-1" /> Paid

                                                                        </Badge>

                                                                    ) : appointment.status === "canceled" ? (

                                                                        <Button

                                                                            variant="outline"

                                                                            size="sm"

                                                                            className="flex items-center gap-1"

                                                                            onClick={() => handleRescheduleClick(appointment)}

                                                                        >

                                                                            <CalendarIcon className="w-4 h-4" /> Reschedule

                                                                        </Button>

                                                                    ) : (

                                                                        <Badge variant="outline" className="ml-auto">

                                                                            Completed

                                                                        </Badge>

                                                                    )}

                                                                </TableCell>

                                                            </motion.tr>

                                                        ))}

                                                    </TableBody>

                                                </Table>

                                            </div>

  

                                            {/* Mobile view - Cards */}

                                            <div className="md:hidden space-y-4">

                                                {filteredAppointments.map((appointment, index) => (

                                                    <motion.div

                                                        key={appointment.id}

                                                        initial={{ opacity: 0, y: 10 }}

                                                        animate={{ opacity: 1, y: 0 }}

                                                        transition={{ duration: 0.3, delay: index * 0.05 }}

                                                    >

                                                        <AppointmentCard

                                                            appointment={appointment}

                                                            onPayment={handlePayment}

                                                            onReschedule={handleRescheduleClick}

                                                        />

                                                    </motion.div>

                                                ))}

                                            </div>

                                        </>

                                    ) : (

                                        <div className="flex flex-col items-center justify-center py-12 text-center">

                                            <div className="bg-muted/30 p-4 rounded-full mb-4">

                                                <AlertCircle className="h-8 w-8 text-muted-foreground" />

                                            </div>

                                            <h3 className="text-lg font-medium mb-1">

                                                No {tabValue !== "all" ? tabValue : ""} appointments found

                                            </h3>

                                            <p className="text-muted-foreground max-w-md">

                                                {searchQuery || statusFilter !== "all"

                                                    ? "Try adjusting your filters to see more results"

                                                    : "You don't have any appointments yet. Schedule your first appointment to get started."}

                                            </p>

                                            {(searchQuery || statusFilter !== "all") && (

                                                <Button

                                                    variant="outline"

                                                    className="mt-4"

                                                    onClick={() => {

                                                        setSearchQuery("")

                                                        setStatusFilter("all")

                                                    }}

                                                >

                                                    Clear Filters

                                                </Button>

                                            )}

                                        </div>

                                    )}

                                </TabsContent>

                            ))}

                        </Tabs>

                    </CardContent>

                </Card>

            </motion.div>

  

            {/* Reschedule Dialog */}

            <Dialog open={isRescheduleOpen} onOpenChange={setIsRescheduleOpen}>

                <DialogContent className="sm:max-w-[425px]">

                    <DialogHeader>

                        <DialogTitle>Reschedule Appointment</DialogTitle>

                        <DialogDescription>

                            Select a new date and time for your appointment with {selectedAppointment?.doctor_name}.

                        </DialogDescription>

                    </DialogHeader>

  

                    <div className="grid gap-4 py-4">

                        <div className="grid gap-2">

                            <label className="text-sm font-medium">Date</label>

                            <Popover>

                                <PopoverTrigger asChild>

                                    <Button

                                        variant="outline"

                                        className={`w-full justify-start text-left font-normal ${!rescheduleDate ? "text-muted-foreground" : ""}`}

                                    >

                                        <CalendarIcon className="mr-2 h-4 w-4" />

                                        {rescheduleDate ? format(rescheduleDate, "PPP") : "Select date"}

                                    </Button>

                                </PopoverTrigger>

                                <PopoverContent className="w-auto p-0" align="start">

                                    <Calendar

                                        mode="single"

                                        selected={rescheduleDate}

                                        onSelect={setRescheduleDate}

                                        initialFocus

                                        disabled={(date) => date < new Date() || date > addDays(new Date(), 90)}

                                    />

                                </PopoverContent>

                            </Popover>

                        </div>

  

                        <div className="grid gap-2">

                            <label className="text-sm font-medium">Time</label>

                            <Select value={rescheduleTime} onValueChange={setRescheduleTime}>

                                <SelectTrigger className={!rescheduleTime ? "text-muted-foreground" : ""}>

                                    <SelectValue placeholder="Select time" />

                                </SelectTrigger>

                                <SelectContent>

                                    {timeSlots.map((time) => (

                                        <SelectItem key={time} value={time}>

                                            {time}

                                        </SelectItem>

                                    ))}

                                </SelectContent>

                            </Select>

                        </div>

                    </div>

  

                    <DialogFooter>

                        <Button variant="outline" onClick={() => setIsRescheduleOpen(false)}>

                            Cancel

                        </Button>

                        <Button onClick={handleRescheduleSubmit}>Confirm Reschedule</Button>

                    </DialogFooter>

                </DialogContent>

            </Dialog>

        </div>

    )

}