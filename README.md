from geopy.geocoders import Nominatim
import os,time
os.system('cls')
print("TOOL GET QUỐC GIA")
print("KẾT QUẢ SẼ ĐƯỢC LƯU RA FILE KETQUA.txt")
input("BẤM ENTER ĐỂ CHỌN FILE CHỨA UID: ")
open_file = input("Input: ")
file = open(open_file,"r",encoding="latin-1").readlines()
time.sleep(1)
print(f"ĐÃ LOAD ĐƯỢC {len(file)} UID")
a=0
for s in file:
	s = s.replace("\n","")
	split_uid = s.split("|")[0]
	split_du = s.split("|")[1]
	split_country = split_du.split(",")
	try:
		sp = split_country[0]
		geolocator = Nominatim(user_agent="my_geocoder")
		location = geolocator.geocode(sp)
		kq = location.address
		tach = str(kq).split(',')
		a+=1
		b = split_uid+" ==>"+tach[len(tach)-1]
		open("KETQUA.txt",'a+',encoding = 'utf-8').write(b+'\n')
		print(f"[{a}]",b)
	except:
		try:
			sp = split_country[1]
			geolocator = Nominatim(user_agent="my_geocoder")
			location = geolocator.geocode(sp)
			kq = location.address
			tach = str(kq).split(',')
			a+=1
			b = split_uid+" ==>"+tach[len(tach)-1]
			open("KETQUA.txt",'a+',encoding = 'utf-8').write(b+'\n')
			print(f"[{a}]",b)
		except:
			try:
				sp = split_country[2]
				geolocator = Nominatim(user_agent="my_geocoder")
				location = geolocator.geocode(sp)
				kq = location.address
				tach = str(kq).split(',')
				a+=1
				b = split_uid+" ==>"+tach[len(tach)-1]
				open("KETQUA.txt",'a+',encoding = 'utf-8').write(b+'\n')
				print(f"[{a}]",b)
			except:
				a+=1
				c = split_uid+' ==> Không get được quốc gia'
				print(f"[{a}]",c)
				open("KETQUA.txt",'a+',encoding = 'utf-8').write(c+'\n')
