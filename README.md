#!usr/bin python3.8
from tkinter import*
import random,math,os
from tkinter import messagebox
class Bill_App:
	def __init__(self,root):
		self.root=root
		self.root.geometry("1350x700+0+0")
		self.root.title("Billing Software")
		bg_color="#b03060"
		title=Label(self.root,text="Billing Software",bd=12,relief=GROOVE,bg=bg_color,fg="white",font=("helwetica",30,"bold"),pady=2).pack(fill=X)

		#========= variables ===========#
		# cosmetics
		self.soap=IntVar()
		self.facecream=IntVar()
		self.facewash=IntVar()
		self.hairspray=IntVar()
		self.hairgel=IntVar()
		self.bodylotion=IntVar()

		#grocery
		self.rice=IntVar()
		self.food_oil=IntVar()
		self.dal=IntVar()
		self.wheat=IntVar()
		self.sugar=IntVar()
		self.tea=IntVar()

		#cold drinks
		self.mazza=IntVar()
		self.coke=IntVar()
		self.frooty=IntVar()
		self.thumbsup=IntVar()
		self.limca=IntVar()
		self.sprite=IntVar()

		#total price
		self.total_cosmetic_price=StringVar()
		self.total_grocery_price=StringVar()
		self.total_cold_drinks_price=StringVar()

		#tax
		self.cosmetic_tax=StringVar()
		self.grocery_tax=StringVar()
		self.cold_drinks_tax=StringVar()

		#customer details
		self.c_name=StringVar()
		self.c_pno=StringVar()
		self.bill_no=StringVar()
		x=random.randint(1000,9999)
		self.bill_no.set(str(x))
		self.search_bill=StringVar()
		f1=LabelFrame(self.root,bd=10,relief=GROOVE,text="Customer Details",font=("times new roman",15,"bold"),fg="gold",bg=bg_color)
		f1.place(x=0,y=80,relwidth=1)

		cname_lbl=Label(f1,text="Customer Name",bg=bg_color,font=("times new roman",18,"bold")).grid(row=0,column=0,padx=20,pady=5)
		cname_txt=Entry(f1,width=15,font="arial 15",textvariable=self.c_name,bd=7,relief=SUNKEN).grid(row=0,column=1,pady=5,padx=10)

		cphone_lbl=Label(f1,text="Phone no",bg=bg_color,font=("times new roman",18,"bold")).grid(row=0,column=2,padx=20,pady=5)
		cphone_txt=Entry(f1,width=15,font="arial 15",textvariable=self.c_pno,bd=7,relief=SUNKEN).grid(row=0,column=3,pady=5,padx=10)

		cbill_lbl=Label(f1,text="Bill number",bg=bg_color,font=("times new roman",18,"bold")).grid(row=0,column=4,padx=20,pady=5)
		cbill_txt=Entry(f1,width=15,font="arial 15",textvariable=self.bill_no,bd=7,relief=SUNKEN).grid(row=0,column=5,pady=5,padx=10)
		bill_btn=Button(f1,text="search",width=10,bd=7,font="arial 12 bold").grid(row=0,column=6,padx=10,pady=10)

		# cosmetic frame
		f2=LabelFrame(self.root,bd=10,relief=GROOVE,text="Cosmetics",font=("times new roman",15,"bold"),fg="gold",bg=bg_color)
		f2.place(x=5,y=180,width=325,height=380)

		bath_lbl=Label(f2,text="Bath Soap",font=("times new roman",16,"bold"),bg=bg_color,fg="black").grid(row=0,column=0,padx=10,pady=10,sticky="w")
		bath_txt=Entry(f2,width=10,font=("times new roman",16,"bold"),textvariable=self.soap,bd=5,relief=SUNKEN).grid(row=0,column=1,padx=10,pady=10)

		face_cream=Label(f2,text="Face cream",font=("times new roman",16,"bold"),bg=bg_color,fg="black").grid(row=1,column=0,padx=10,pady=10,sticky="w")
		face_cream_txt=Entry(f2,width=10,font=("times new roman",16,"bold"),textvariable=self.facecream,bd=5,relief=SUNKEN).grid(row=1,column=1,padx=10,pady=10)

		face_wash=Label(f2,text="Face wash",font=("times new roman",16,"bold"),bg=bg_color,fg="black").grid(row=2,column=0,padx=10,pady=10,sticky="w")
		face_wash_txt=Entry(f2,width=10,font=("times new roman",16,"bold"),textvariable=self.facewash,bd=5,relief=SUNKEN).grid(row=2,column=1,padx=10,pady=10)

		hair_spray=Label(f2,text="Hair spray",font=("times new roman",16,"bold"),bg=bg_color,fg="black").grid(row=3,column=0,padx=10,pady=10,sticky="w")
		hair_spray_txt=Entry(f2,width=10,font=("times new roman",16,"bold"),textvariable=self.hairspray,bd=5,relief=SUNKEN).grid(row=3,column=1,padx=10,pady=10)

		hair_gel=Label(f2,text="Hair gel",font=("times new roman",16,"bold"),bg=bg_color,fg="black").grid(row=4,column=0,padx=10,pady=10,sticky="w")
		hair_gel_txt=Entry(f2,width=10,font=("times new roman",16,"bold"),textvariable=self.hairgel,bd=5,relief=SUNKEN).grid(row=4,column=1,padx=10,pady=10)

		body_lotion=Label(f2,text="Body Lotion",font=("times new roman",16,"bold"),bg=bg_color,fg="black").grid(row=5,column=0,padx=10,pady=10,sticky="w")
		body_lotion_txt=Entry(f2,width=10,font=("times new roman",16,"bold"),textvariable=self.bodylotion,bd=5,relief=SUNKEN).grid(row=5,column=1,padx=10,pady=10)

		# grocery frame
		f3=LabelFrame(self.root,bd=10,relief=GROOVE,text="Grocery",font=("times new roman",15,"bold"),fg="gold",bg=bg_color)
		f3.place(x=330,y=180,width=325,height=380)

		rice_lbl=Label(f3,text="Rice",font=("times new roman",16,"bold"),bg=bg_color,fg="black").grid(row=0,column=0,padx=10,pady=10,sticky="w")
		rice_txt=Entry(f3,width=10,font=("times new roman",16,"bold"),textvariable=self.rice,bd=5,relief=SUNKEN).grid(row=0,column=1,padx=10,pady=10)

		food_oil=Label(f3,text="Food oil",font=("times new roman",16,"bold"),bg=bg_color,fg="black").grid(row=1,column=0,padx=10,pady=10,sticky="w")
		food_oil_txt=Entry(f3,width=10,font=("times new roman",16,"bold"),textvariable=self.food_oil,bd=5,relief=SUNKEN).grid(row=1,column=1,padx=10,pady=10)

		daal_lbl=Label(f3,text="Daal",font=("times new roman",16,"bold"),bg=bg_color,fg="black").grid(row=2,column=0,padx=10,pady=10,sticky="w")
		daal_txt=Entry(f3,width=10,font=("times new roman",16,"bold"),textvariable=self.dal,bd=5,relief=SUNKEN).grid(row=2,column=1,padx=10,pady=10)

		wheat=Label(f3,text="Wheat",font=("times new roman",16,"bold"),bg=bg_color,fg="black").grid(row=3,column=0,padx=10,pady=10,sticky="w")
		wheat_txt=Entry(f3,width=10,font=("times new roman",16,"bold"),textvariable=self.wheat,bd=5,relief=SUNKEN).grid(row=3,column=1,padx=10,pady=10)

		sugar_lbl=Label(f3,text="Sugar",font=("times new roman",16,"bold"),bg=bg_color,fg="black").grid(row=4,column=0,padx=10,pady=10,sticky="w")
		sugar_txt=Entry(f3,width=10,font=("times new roman",16,"bold"),textvariable=self.sugar,bd=5,relief=SUNKEN).grid(row=4,column=1,padx=10,pady=10)

		tea_lbl=Label(f3,text="Tea",font=("times new roman",16,"bold"),bg=bg_color,fg="black").grid(row=5,column=0,padx=10,pady=10,sticky="w")
		tea_txt=Entry(f3,width=10,font=("times new roman",16,"bold"),textvariable=self.tea,bd=5,relief=SUNKEN).grid(row=5,column=1,padx=10,pady=10)

		# cold drinks frame
		f4=LabelFrame(self.root,bd=10,relief=GROOVE,text="Cold drinks",font=("times new roman",15,"bold"),fg="gold",bg=bg_color)
		f4.place(x=655,y=180,width=325,height=380)

		mazza_lbl=Label(f4,text="Mazza",font=("times new roman",16,"bold"),bg=bg_color,fg="black").grid(row=0,column=0,padx=10,pady=10,sticky="w")
		mazza_txt=Entry(f4,width=10,font=("times new roman",16,"bold"),textvariable=self.mazza,bd=5,relief=SUNKEN).grid(row=0,column=1,padx=10,pady=10)

		coke_lbl=Label(f4,text="Coke",font=("times new roman",16,"bold"),bg=bg_color,fg="black").grid(row=1,column=0,padx=10,pady=10,sticky="w")
		coke_txt=Entry(f4,width=10,font=("times new roman",16,"bold"),textvariable=self.coke,bd=5,relief=SUNKEN).grid(row=1,column=1,padx=10,pady=10)

		frooty_lbl=Label(f4,text="Frooty",font=("times new roman",16,"bold"),bg=bg_color,fg="black").grid(row=2,column=0,padx=10,pady=10,sticky="w")
		frooty_txt=Entry(f4,width=10,font=("times new roman",16,"bold"),textvariable=self.frooty,bd=5,relief=SUNKEN).grid(row=2,column=1,padx=10,pady=10)

		thumbs_up_lbl=Label(f4,text="Thumbs up",font=("times new roman",16,"bold"),bg=bg_color,fg="black").grid(row=3,column=0,padx=10,pady=10,sticky="w")
		thumbs_up_txt=Entry(f4,width=10,font=("times new roman",16,"bold"),textvariable=self.thumbsup,bd=5,relief=SUNKEN).grid(row=3,column=1,padx=10,pady=10)

		limca_lbl=Label(f4,text="Limca",font=("times new roman",16,"bold"),bg=bg_color,fg="black").grid(row=4,column=0,padx=10,pady=10,sticky="w")
		limca_txt=Entry(f4,width=10,font=("times new roman",16,"bold"),textvariable=self.limca,bd=5,relief=SUNKEN).grid(row=4,column=1,padx=10,pady=10)

		sprite_lbl=Label(f4,text="Sprite",font=("times new roman",16,"bold"),bg=bg_color,fg="black").grid(row=5,column=0,padx=10,pady=10,sticky="w")
		sprite_txt=Entry(f4,width=10,font=("times new roman",16,"bold"),textvariable=self.sprite,bd=5,relief=SUNKEN).grid(row=5,column=1,padx=10,pady=10)

		#bill area
		f5=Frame(self.root,bd=10,relief=GROOVE)
		f5.place(x=985,y=180,width=380,height=380)
		bill_title=Label(f5,text="Bill Area",font="arial 15 bold",bd=7,relief=GROOVE).pack(fill=X)
		scrol_y=Scrollbar(f5,orient=VERTICAL)
		self.txtarea=Text(f5,yscrollcommand=scrol_y.set)
		scrol_y.pack(side=RIGHT,fill=Y)
		scrol_y.config(command=self.txtarea.yview)
		self.txtarea.pack()

		#bill menu
		f6=LabelFrame(self.root,bd=10,relief=GROOVE,text="Bill menu",font=("times new roman",15,"bold"),fg="gold",bg=bg_color)
		f6.place(x=0,y=560,relwidth=1,height=140)

		m1_lbl=Label(f6,text="Total Cosmetic Price",bg=bg_color,fg="black",font=("times new roman",15,"bold")).grid(row=0,column=0,padx=0,pady=1,sticky="w")
		m1_txt=Entry(f6,width=18,font="arial 10 bold",textvariable=self.total_cosmetic_price,bd=7,relief=SUNKEN).grid(row=0,column=1,padx=2,pady=1)

		m2_lbl=Label(f6,text="Total grocery Price",bg=bg_color,fg="black",font=("times new roman",15,"bold")).grid(row=1,column=0,padx=0,pady=1,sticky="w")
		m2_txt=Entry(f6,width=18,font="arial 10 bold",textvariable=self.total_grocery_price,bd=7,relief=SUNKEN).grid(row=1,column=1,padx=2,pady=1)

		m3_lbl=Label(f6,text="Total Cold drinks Price",bg=bg_color,fg="black",font=("times new roman",15,"bold")).grid(row=2,column=0,padx=0,pady=1,sticky="w")
		m3_txt=Entry(f6,width=18,font="arial 10 bold",bd=7,textvariable=self.total_cold_drinks_price,relief=SUNKEN).grid(row=2,column=1,padx=2,pady=1)


		c1_lbl=Label(f6,text="Cosmetic tax",bg=bg_color,fg="black",font=("times new roman",15,"bold")).grid(row=0,column=2,padx=5,pady=1,sticky="w")
		c1_txt=Entry(f6,width=18,font="arial 10 bold",textvariable=self.cosmetic_tax,bd=7,relief=SUNKEN).grid(row=0,column=3,padx=4,pady=1)

		c2_lbl=Label(f6,text="Grocery tax",bg=bg_color,fg="black",font=("times new roman",15,"bold")).grid(row=1,column=2,padx=5,pady=1,sticky="w")
		c2_txt=Entry(f6,width=18,font="arial 10 bold",textvariable=self.grocery_tax,bd=7,relief=SUNKEN).grid(row=1,column=3,padx=4,pady=1)

		c3_lbl=Label(f6,text="Cold drinks tax",bg=bg_color,fg="black",font=("times new roman",15,"bold")).grid(row=2,column=2,padx=5,pady=1,sticky="w")
		c3_txt=Entry(f6,width=18,font="arial 10 bold",textvariable=self.cold_drinks_tax,bd=7,relief=SUNKEN).grid(row=2,column=3,padx=4,pady=1)

		btn_F=Frame(f6,bd=7,relief=GROOVE)
		btn_F.place(x=670,width=650,height=105)


		total_btn=Button(btn_F,command=self.total,text="Total",bg="blue",bd=5,fg="white",width=10,font="Arial 15 bold",pady=15).grid(row=0,column=4,padx=5,pady=5)
		clear_btn=Button(btn_F,text="Clear",bg="blue",bd=5,fg="white",width=10,font="Arial 15 bold",pady=15).grid(row=0,column=5,padx=5,pady=5)
		g_bill_btn=Button(btn_F,text="Generate Bill",command=self.bill_area,bg="blue",bd=5,fg="white",width=10,font="Arial 15 bold",pady=15).grid(row=0,column=6,padx=5,pady=5)
		exit_btn=Button(btn_F,text="Exit",bg="blue",bd=5,fg="white",width=10,font="Arial 15 bold",pady=15).grid(row=0,column=7,padx=5,pady=5)

		self.welcome_bill()

	def total(self):
		self.c_s_p=self.soap.get()*40
		self.c_fc_p=self.facecream.get()*120
		self.c_fw_p=self.facewash.get()*60
		self.c_hs_p=self.hairspray.get()*180
		self.c_hg_p=self.hairgel.get()*140
		self.c_bl_p=self.bodylotion.get()*180
		
		self.g_rc_p=self.rice.get()*70
		self.g_fo_p=self.food_oil.get()*100
		self.g_dl_p=self.dal.get()*60
		self.g_wt_p=(self.wheat.get()*90)
		self.g_sg_p=self.sugar.get()*40
		self.g_te_p=self.tea.get()*150
		
		self.cd_ma_p=self.mazza.get()*40
		self.cd_co_p=self.coke.get()*30
		self.cd_fr_p=self.frooty.get()*35
		self.cd_th_p=self.thumbsup.get()*30
		self.cd_li_p=self.limca.get()*50
		self.cd_sp_p=self.sprite.get()*40
		self.cosmetic_price=float(
								self.c_s_p+
								self.c_fc_p+
								self.c_fw_p+
								self.c_hs_p+
								self.c_hg_p+
								self.c_bl_p
								)
		self.total_cosmetic_price.set("Rs."+str(self.cosmetic_price))
		self.c_tax=round((self.cosmetic_price*0.05),2)
		self.cosmetic_tax.set("Rs."+str(self.c_tax))

		self.grocery_price=float(
								self.g_rc_p+
								self.g_fo_p+
								self.g_dl_p+
								self.g_wt_p+
								self.g_sg_p+
								self.g_te_p
								)
		self.total_grocery_price.set("Rs."+str(self.grocery_price))
		self.g_tax=round((self.grocery_price*0.1),2)
		self.grocery_tax.set("Rs"+str(self.g_tax))


		self.cold_drinks_price=float(
								self.cd_ma_p+
								self.cd_co_p+
								self.cd_fr_p+
								self.cd_th_p+
								self.cd_li_p+
								self.cd_sp_p
								)
		self.total_cold_drinks_price.set("Rs."+str(self.cold_drinks_price))
		self.cl_tax=round((self.cold_drinks_price*0.15),2)
		self.cold_drinks_tax.set("Rs."+str(self.cl_tax))
		self.Total_bill=float(self.cosmetic_price+self.grocery_price+self.cold_drinks_price+self.c_tax+self.g_tax+self.cl_tax)

	def welcome_bill(self):
		self.txtarea.delete('1.0',END)
		self.txtarea.insert(END,"\tWelcome Webcode Retail")
		self.txtarea.insert(END,f"\nBill number:{self.bill_no.get()}")
		self.txtarea.insert(END,f"\nCustomer Name:{self.c_name.get()}")
		self.txtarea.insert(END,f"\nPhone number:{self.c_pno.get()}")
		self.txtarea.insert(END,f"\n==========================================")
		self.txtarea.insert(END,f"\nProducts\t\tQty\t\tprice")
		self.txtarea.insert(END,f"\n==========================================")
	def bill_area(self):
		if self.c_name.get()=="" or self.c_pno.get()=="":
			messagebox.showerror("Error:","customer details are must!")
		elif self.total_cosmetic_price.get()=="Rs.0.0" and self.total_grocery_price.get()=="Rs.0.0" and self.total_cold_drinks_price.get()=="Rs.0.0":
			messagebox.showerror("Error:","No product purchased!")
		else:
			self.welcome_bill()

			#cosmetics
			if self.soap.get()!=0:
				self.txtarea.insert(END,f"\nBath Soap\t\t{self.soap.get()}\t\t{self.c_s_p}")
			if self.facecream.get()!=0:
				self.txtarea.insert(END,f"\nFace cream\t\t{self.facecream.get()}\t\t{self.c_fc_p}")
			if self.facewash.get()!=0:
				self.txtarea.insert(END,f"\nFace wash\t\t{self.facewash.get()}\t\t{self.c_fw_p}")
			if self.hairspray.get()!=0:
				self.txtarea.insert(END,f"\nHair spray\t\t{self.hairspray.get()}\t\t{self.c_hs_p}")
			if self.hairgel.get()!=0:
				self.txtarea.insert(END,f"\nHair gel\t\t{self.hairgel.get()}\t\t{self.c_hg_p}")
			if self.bodylotion.get()!=0:
				self.txtarea.insert(END,f"\nBody lotion\t\t{self.bodylotion.get()}\t\t{self.c_bl_p}")

			# grocery
			if self.rice.get()!=0:
				self.txtarea.insert(END,f"\nRice\t\t\t{self.rice.get()}\t\t{self.g_rc_p}")
			if self.food_oil.get()!=0:
				self.txtarea.insert(END,f"\nFood Oil\t\t{self.food_oil.get()}\t\t{self.g_fo_p}")
			if self.dal.get()!=0:
				self.txtarea.insert(END,f"\nDaal\t\t\t{self.dal.get()}\t\t{self.g_dl_p}")
			if self.wheat.get()!=0:
				self.txtarea.insert(END,f"\nWheat\t\t\t{self.wheat.get()}\t\t{self.g_wt_p}")
			if self.sugar.get()!=0:
				self.txtarea.insert(END,f"\nSugar\t\t\t{self.sugar.get()}\t\t{self.g_sg_p}")
			if self.tea.get()!=0:
				self.txtarea.insert(END,f"\nTea\t\t\t{self.tea.get()}\t\t{self.g_te_p}")

			#cold_drinks
			if self.mazza.get()!=0:
				self.txtarea.insert(END,f"\nMazza\t\t\t{self.mazza.get()}\t\t{self.cd_ma_p}")
			if self.coke.get()!=0:
				self.txtarea.insert(END,f"\nCoke\t\t\t{self.coke.get()}\t\t{self.cd_co_p}")
			if self.frooty.get()!=0:
				self.txtarea.insert(END,f"\nFrooty\t\t\t{self.frooty.get()}\t\t{self.cd_fr_p}")
			if self.thumbsup.get()!=0:
				self.txtarea.insert(END,f"\nThumbs up\t\t{self.thumbsup.get()}\t\t{self.cd_th_p}")
			if self.limca.get()!=0:
				self.txtarea.insert(END,f"\nLimca\t\t\t{self.limca.get()}\t\t{self.cd_li_p}")
			if self.sprite.get()!=0:
				self.txtarea.insert(END,f"\nSprite\t\t\t{self.sprite.get()}\t\t{self.cd_sp_p}")

			self.txtarea.insert(END,f"\n------------------------------------------")
			if self.cosmetic_tax.get()!="Rs. 0.0":
				self.txtarea.insert(END,f"\nCosmetic Tax\t\t\t{self.cosmetic_tax.get()}")
			
			if self.grocery_tax.get()!="Rs. 0.0":
				self.txtarea.insert(END,f"\nGrocery Tax\t\t\t{self.grocery_tax.get()}")

			if self.cold_drinks_tax.get()!="Rs. 0.0":
				self.txtarea.insert(END,f"\nCold Drinks Tax\t\t\t{self.cold_drinks_tax.get()}")
				
			
			self.txtarea.insert(END,f"\n------------------------------------------\n")

			self.txtarea.insert(END,f"\n==========================================")
			self.txtarea.insert(END,f"\nTotal bill \t\t\tRs.{self.Total_bill}")
			self.txtarea.insert(END,f"\n==========================================")

			self.save_bill()
	
	def save_bill(self):
		op=messagebox.askyesno("Save Bill","Do you want to save the bill?")
		if op>0:
			self.bill_data=self.txtarea.get('1.0',END)
			f1=open("bills/"+str(self.bill_no.get())+".txt","w")
			f1.write(self.bill_data)
			f1.close()
			messagebox.showinfo("Saved",f"Bill no. :{self.bill_no.get()} Saved successfully!")
		else:
			return

	

			




root=Tk()
		
obj=Bill_App(root)
root.mainloop()
