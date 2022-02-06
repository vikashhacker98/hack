gg.toast("■□□□□□□□□□𝟭𝟬%")
gg.sleep(200)
gg.toast("■■□□□□□□□□𝟮𝟬%")
gg.sleep(200)
gg.toast("■■■□□□□□□□𝟯𝟬%")
gg.sleep(200)
gg.toast("■■■■□□□□□□𝟰𝟬%")
gg.sleep(200)
gg.toast("■■■■■□□□□□𝟱𝟬%")
gg.sleep(200)
gg.toast("■■■■■■□□□□𝟲𝟬%")
gg.sleep(200)
gg.toast("■■■■■■■□□□𝟳𝟬%")
gg.sleep(200)
gg.toast("■■■■■■■■□□𝟴𝟬%")
gg.sleep(200)
gg.toast("■■■■■■■■■□𝟵𝟬%")
gg.sleep(200)
gg.toast("■■■■■■■■■■𝟭𝟬𝟬%")
gg.sleep(500)
function split(szFullString, szSeparator) local nFindStartIndex = 1 local nSplitIndex = 1 local nSplitArray = {} while true do local nFindLastIndex = string.find (szFullString, szSeparator, nFindStartIndex) if not nFindLastIndex then nSplitArray[nSplitIndex] = string.sub(szFullString, nFindStartIndex, string.len (szFullString)) break end nSplitArray[nSplitIndex] = string.sub (szFullString, nFindStartIndex, nFindLastIndex - 1) nFindStartIndex = nFindLastIndex + string.len (szSeparator) nSplitIndex = nSplitIndex + 1 end return nSplitArray end function xgxc(szpy, qmxg) for x = 1, #(qmxg) do xgpy = szpy + qmxg[x]["offset"] xglx = qmxg[x]["type"] xgsz = qmxg[x]["value"] xgdj = qmxg[x]["freeze"] if xgdj == nil or xgdj == "" then gg.setValues({[1] = {address = xgpy, flags = xglx, value = xgsz}}) else gg.addListItems({[1] = {address = xgpy, flags = xglx, freeze = xgdj, value = xgsz}}) end xgsl = xgsl + 1 xgjg = true end end function xqmnb(qmnb) gg.clearResults() gg.setRanges(qmnb[1]["memory"]) gg.searchNumber(qmnb[3]["value"], qmnb[3]["type"]) if gg.getResultCount() == 0 then gg.toast(qmnb[2]["name"] .. "开启失败") else gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) if gg.getResultCount() == 0 then gg.toast(qmnb[2]["name"] .. "开启失败") else sl = gg.getResults(999999) sz = gg.getResultCount() xgsl = 0 if sz > 999999 then sz = 999999 end for i = 1, sz do pdsz = true for v = 4, #(qmnb) do if pdsz == true then pysz = {} pysz[1] = {} pysz[1].address = sl[i].address + qmnb[v]["offset"] pysz[1].flags = qmnb[v]["type"] szpy = gg.getValues(pysz) pdpd = qmnb[v]["lv"] .. ";" .. szpy[1].value szpd = split(pdpd, ";") tzszpd = szpd[1] pyszpd = szpd[2] if tzszpd == pyszpd then pdjg = true pdsz = true else pdjg = false pdsz = false end end end if pdjg == true then szpy = sl[i].address xgxc(szpy, qmxg) end end if xgjg == true then gg.toast(qmnb[2]["name"] .. "开启成功，一共修改" .. xgsl .. "条数据") else gg.toast(qmnb[2]["name"] .. "未搜索到数据，开启失败") end end end end function SearchWrite(Search, Write, Type) gg.clearResults() gg.setVisible(false) gg.searchNumber(Search[1][1], Type) local count = gg.getResultCount() local result = gg.getResults(count) gg.clearResults() local data = {} local base = Search[1][2] if (count > 0) then for i, v in ipairs(result) do v.isUseful = true end for k=2, #Search do local tmp = {} local offset = Search[k][2] - base local num = Search[k][1] for i, v in ipairs(result) do tmp[#tmp+1] = {} tmp[#tmp].address = v.address + offset tmp[#tmp].flags = v.flags end tmp = gg.getValues(tmp) for i, v in ipairs(tmp) do if ( tostring(v.value) ~= tostring(num) ) then result[i].isUseful = false end end end for i, v in ipairs(result) do if (v.isUseful) then data[#data+1] = v.address end end if (#data > 0) then local t = {} local base = Search[1][2] for i=1, #data do for k, w in ipairs(Write) do offset = w[2] - base t[#t+1] = {} t[#t].address = data[i] + offset t[#t].flags = Type t[#t].value = w[1] if (w[3] == true) then local item = {} item[#item+1] = t[#t] item[#item].freeze = true gg.addListItems(item) end end end gg.setValues(t) gg.toast("开启成功，一共修改"..#t.."条数据") gg.addListItems(t) else gg.toast("未搜索到数据，开启失败", false) return false end else gg.toast("Not Found") return false end end
function split(szFullString, szSeparator) local nFindStartIndex = 1 local nSplitIndex = 1 local nSplitArray = {} while true do local nFindLastIndex = string.find(szFullString, szSeparator, nFindStartIndex) if not nFindLastIndex then nSplitArray[nSplitIndex] = string.sub(szFullString, nFindStartIndex, string.len(szFullString)) break end nSplitArray[nSplitIndex] = string.sub(szFullString, nFindStartIndex, nFindLastIndex - 1) nFindStartIndex = nFindLastIndex + string.len(szSeparator) nSplitIndex = nSplitIndex + 1 end return nSplitArray end function xgxc(szpy, qmxg) for x = 1, #(qmxg) do xgpy = szpy + qmxg[x]["offset"] xglx = qmxg[x]["type"] xgsz = qmxg[x]["value"] gg.setValues({[1] = {address = xgpy, flags = xglx, value = xgsz}}) xgsl = xgsl + 1 end end function xqmnb(qmnb) gg.clearResults() gg.setRanges(qmnb[1]["memory"]) gg.searchNumber(qmnb[3]["value"], qmnb[3]["type"]) if gg.getResultCount() == 0 then gg.toast(qmnb[2]["name"] .. "") else gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) if gg.getResultCount() == 0 then gg.toast(qmnb[2]["name"] .. "") else sl = gg.getResults(999999) sz = gg.getResultCount() xgsl = 0 if sz > 999999 then sz = 999999 end for i = 1, sz do pdsz = true for v = 4, #(qmnb) do if pdsz == true then pysz = {} pysz[1] = {} pysz[1].address = sl[i].address + qmnb[v]["offset"] pysz[1].flags = qmnb[v]["type"] szpy = gg.getValues(pysz) pdpd = qmnb[v]["lv"] .. ";" .. szpy[1].value szpd = split(pdpd, ";") tzszpd = szpd[1] pyszpd = szpd[2] if tzszpd == pyszpd then pdjg = true pdsz = true else pdjg = false pdsz = false end end end if pdjg == true then szpy = sl[i].address xgxc(szpy, qmxg) xgjg = true end end if xgjg == true then gg.toast(qmnb[2]["name"] .. "" .. xgsl .. "") else gg.toast(qmnb[2]["name"] .. "") end end end end
function setvalue(address,flags,value) local tt={} tt[1]={} tt[1].address=address tt[1].flags=flags tt[1].value=value gg.setValues(tt) end
function setvalue(address,flags,value) local tt={} tt[1]={} tt[1].address=address tt[1].flags=flags tt[1].value=value gg.setValues(tt) end
function PS() end
function setvalue(address,flags,value) PS('Modify address value (address, value type, value to be modified)') local tt={} tt[1]={} tt[1].address=address tt[1].flags=flags tt[1].value=value gg.setValues(tt) end
function split(szFullString, szSeparator) local nFindStartIndex = 1 local nSplitIndex = 1 local nSplitArray = {} while true do local nFindLastIndex = string.find(szFullString, szSeparator, nFindStartIndex) if not nFindLastIndex then nSplitArray[nSplitIndex] = string.sub(szFullString, nFindStartIndex, string.len(szFullString)) break end nSplitArray[nSplitIndex] = string.sub(szFullString, nFindStartIndex, nFindLastIndex - 1) nFindStartIndex = nFindLastIndex + string.len(szSeparator) nSplitIndex = nSplitIndex + 1 end return nSplitArray end function xgxc(szpy, qmxg) for x = 1, #(qmxg) do xgpy = szpy + qmxg[x]["offset"] xglx = qmxg[x]["type"] xgsz = qmxg[x]["value"] xgdj = qmxg[x]["freeze"] if xgdj == nil or xgdj == "" then gg.setValues({[1] = {address = xgpy, flags = xglx, value = xgsz}}) else gg.addListItems({[1] = {address = xgpy, flags = xglx, freeze = xgdj, value = xgsz}}) end xgsl = xgsl + 1 xgjg = true end end function xqmnb(qmnb) gg.clearResults() gg.setRanges(qmnb[1]["memory"]) gg.searchNumber(qmnb[3]["value"], qmnb[3]["type"]) if gg.getResultCount() == 0 then gg.toast(qmnb[2]["name"] .. "open失败") else gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) if gg.getResultCount() == 0 then gg.toast(qmnb[2]["name"] .. "open失败") else sl = gg.getResults(999999) sz = gg.getResultCount() xgsl = 0 if sz > 999999 then sz = 999999 end for i = 1, sz do pdsz = true for v = 4, #(qmnb) do if pdsz == true then pysz = {} pysz[1] = {} pysz[1].address = sl[i].address + qmnb[v]["offset"] pysz[1].flags = qmnb[v]["type"] szpy = gg.getValues(pysz) pdpd = qmnb[v]["lv"] .. ";" .. szpy[1].value szpd = split(pdpd, ";") tzszpd = szpd[1] pyszpd = szpd[2] if tzszpd == pyszpd then pdjg = true pdsz = true else pdjg = false pdsz = false end end end if pdjg == true then szpy = sl[i].address xgxc(szpy, qmxg) end end if xgjg == true then gg.toast(qmnb[2]["name"] .. "open,共修改" .. xgsl .. "条数据") else gg.toast(qmnb[2]["name"] .. "open失败") end end end end --@Saifu_hkc
function setvalue(address,flags,value) local tt={} tt[1]={} tt[1].address=address tt[1].flags=flags tt[1].value=value gg.setValues(tt) end
function readWrite(Search,Get,Type,Range,Name) gg["clearResults"]() gg["setRanges"](Range) gg["setVisible"](false) if Search[1][1]~=false then _G["gg"]["searchAddress"](Search[1][1],0xFFFFFFFF,Search[1][4] or Type,_G["gg"]["SIGN_EQUAL"],Search[1][5] or 1,Search[1][6] or -1) end gg["searchNumber"](Search[1][2],Search[1][4] or Type,false,_G["gg"]["SIGN_EQUAL"],Search[1][5] or 1,Search[1][6] or -1) local count=gg["getResultCount"]() local result=gg["getResults"](count) gg["clearResults"]() local data={} local base=Search[1][3] if (count > 0) then for i,v in ipairs(result) do v.isUseful=true end for k=2,#Search do local tmp={} local offset=Search[k][2] - base local num=Search[k][1] for i,v in ipairs(result) do tmp[#tmp+1]={} tmp[#tmp].address=v.address+offset tmp[#tmp].flags=Search[k][3] or Type end tmp=gg["getValues"](tmp) for i,v in ipairs(tmp) do if v.flags==16 or v.flags==64 then values=tostring(v.value):sub(1,6) num=tostring(num):sub(1,6) else values=v.value end if tostring(values)~=tostring(num) then result[i].isUseful=false end end end for i,v in ipairs(result) do if (v.isUseful) then data[#data+1]=v.address end end if (#data > 0) then local t,t_={},{} local base=Search[1][3] for i=1,#data do for k,w in ipairs(Get) do offset=w[2] - base if w[1]==false then t_[#t_+1]={} t_[#t_].address=data[i]+offset t_[#t_].flags=Type th_=(th_) and th_+1 or 1 else t[#t+1]={} t[#t].address=data[i]+offset t[#t].flags=w[3] or Type t[#t].value=w[1] tg_=(tg_) and tg_+1 or 1 if (w[4]==true) then local item={} item[#item+1]=t[#t] item[#item].freeze=w[4] gg["addListItems"](item) end end end end tg=(tg_) and "\n modify"..tg_.."data" or "" th=(th_) and "" or "" gg["setValues"](t) t_=gg["getValues"](t_) gg["loadResults"](t_) gg["toast"]("\n"..Name..tg) tg_,th_=nil,nil else gg["toast"]("Not searchable",false) return false end else gg["toast"]("Not searchable") return false end end
 
gg.alert("❮▬▬▬✧✧✧✧▬▬▬❯\n[👑]sᴄʀɪᴘᴛ ➪ ᴠɪᴋᴀsʜ sɪɴɢʜ\n[👑]ɢᴀᴍᴇ ➪ ᴘᴜʙɢ ʟɪᴛᴇ\n[👑]ᴅᴍ ➪ Vɪᴋᴀsʜ Hᴀᴄᴋᴇʀ\n[👑]ᴅᴀᴛᴇ ➪ "..os.date("%d/%m/%Y").."\n❮▬▬▬✧✧✧✧▬▬▬❯")
 
function START()
VG = gg.multiChoice({
"╔✧[👑]\n╚✧Bʏᴘᴀss Lᴏɢᴏ",  ---1
"╔✧[👑]\n╚✧Bʏᴘᴀss Lᴏʙʙʏ", ---2
"╔✧[👑]\n╚✧Bʟᴏᴄᴋ Rᴇᴘᴏʀᴛ", ---3
"╔✧[👑]\n╚✧Aʟʟ Bʀᴜᴛᴀʟ", ---4
"╔✧[👑]\n╚✧Aɪᴍʙᴏᴛ", ---5
"╔✧[👑]\n╚✧Sᴄᴏᴘᴇ Esᴘ",----6
"╔✧[👑]\n╚✧Fʟᴀsʜ Mᴇɴᴜ",----7
"╔✧[👑]\n╚✧Cᴀʀ Jᴜᴍᴘ",-----8
"╔✧[👑]\n╚✧Cᴀʀ Sᴘᴇᴇᴅ",----9
"╔✧[👑]\n╚✧Mɪᴄʀᴏ Sᴘᴇᴇᴅ",-----10
"╔✧[👑]\n╚✧Exɪᴛ Sᴄʀɪᴘᴛ",----11
 
}, nil, (os.date("❮▬▬▬✧✧✧✧▬▬▬❯\n[👑]sᴄʀɪᴘᴛ ➪ ᴠɪᴋᴀsʜ sɪɴɢʜ\n[👑]ɢᴀᴍᴇ ➪ ᴘᴜʙɢ ʟɪᴛᴇ\n[👑]ᴅᴍ ➪ Vɪᴋᴀsʜ Hᴀᴄᴋᴇʀ\n[👑]ᴅᴀᴛᴇ ➪ "..os.date("%d/%m/%Y").."\n❮▬▬▬✧✧✧✧▬▬▬❯")))
 
 
if VG == nil then else
if VG[1] == true then
ch1()
end
if VG[2] == true then
ch2()
end
if VG[3] == true then
ch3()
end
if VG[4] == true then
ch4()
end
if VG[5] == true then
ch5()
end
if VG[6] == true then
ch6()
end
if VG[7] == true then
ch7()
end
if VG[8] == true then
ch8()
end
if VG[9] == true then
ch9()
end
if VG[10] == true then
ch10()
end
if VG[11] == true then
ch11()
end
 
end
PUBGMH = -1
end
 
 
function ch1()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("620137442967552;564058054983680")
gg.refineNumber("620137442967552")
gg.getResults(50000)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("578351706144768;564058054983680")
gg.refineNumber("578351706144768")
gg.getResults(50000)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("577252194516992;564058054983680")
gg.refineNumber("577252194516992")
gg.getResults(50000)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("579451217772544;564058054983680")
gg.refineNumber("579451217772544;")
gg.getResults(50000)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber(":com.tencent.iglite.ztf", gg.TYPE_BYTE)
gg.getResults(50000)
gg.editAll("119", gg.TYPE_BYTE)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber(":com.tencent.iglite.ztf", gg.TYPE_BYTE)
gg.getResults(50000)
gg.editAll("119", gg.TYPE_BYTE)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("582749752655872;564058054983680")
gg.refineNumber("582749752655872;")
gg.getResults(50000)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("573953659633664;564058054983680")
gg.refineNumber("573953659633664")
gg.getResults(50000)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("582749752655872;564058054983680")
gg.refineNumber("582749752655872")
gg.getResults(50000)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.alert("👑Aʟʟ Tʜɪʀᴅ Pᴀʀᴛʏ Fɪxᴇᴅ Nᴏᴡ Gᴏ Lᴏʙʙʏ Aɴᴅ Aᴘᴘʟʏ Lᴏʙʙʏ Bʏᴘᴀss👑")
end
 
function ch2()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("620137442967552;564058054983680", gg.TYPE_QWORD)
gg.refineNumber("620137442967552", gg.TYPE_QWORD)
gg.getResults(50000)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("578351706144768;564058054983680", gg.TYPE_QWORD)
gg.refineNumber("578351706144768", gg.TYPE_QWORD)
gg.getResults(62877)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.searchNumber("577252194516992;564058054983680", gg.TYPE_QWORD)
gg.refineNumber("577252194516992", gg.TYPE_QWORD)
gg.getResults(50010)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("909391408")
gg.getResults(62877)
gg.editAll("1089886885", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("909391408")
gg.getResults(999)
gg.editAll("1089886885", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("67633927;67109377")
gg.getResults(50000)
gg.editAll("67633927", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("67109390;67114093")
gg.getResults(50000)
gg.editAll("67633927", gg.TYPE_DWORD)
gg.clearResults()
gg.alert("👑Bʏᴘᴀss Lᴏʙʙʏ Aᴄᴛɪᴠᴀᴛᴇᴅ Nᴏᴡ Gᴏ Iᴄᴇʟᴀɴᴅ Aɴᴅ Aᴘʟʟʏ Rᴇᴘᴏʀᴛ Bʟᴏᴄᴋ Eᴠᴇʀʏ Mᴀᴛᴄʜ👑")
end
 
function ch3()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("524304", gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("29793", gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("41097", gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("34842", gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber('"2002204"',gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("459861", gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("925013", gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("19970", gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("786544", gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("909391408", gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber('"3158585"',gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber('"2002006"',gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber('"3159606"',gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber('"2493002"',gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber('"2001001"',gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.alert("👑Rᴇᴘᴏʀᴛ Bʟᴏᴄᴋ Aᴄᴛɪᴠᴀᴛᴇᴅ Nᴏᴡ Sᴛᴀʀᴛ Aʟʟ Hᴀᴄᴋs Nᴏ Aɴʏ Bᴀɴ👑")
end
 
function ch4()
gg.clearResults()
so=gg.getRangesList('libUE4.so')[1].start
py=0x216F8F8
setvalue(so+py,16,0)
gg.toast("Dᴇsᴇʀᴛ Mᴀᴘ")
so=gg.getRangesList('libUE4.so')[1].start
py=0xDA9058
setvalue(so+py,16,0)
gg.toast("Lᴇss Rᴇᴄᴏɪʟ")
so = gg.getRangesList("libUE4.so")[1].start
py = 18242552
setvalue(so + py, 16, 0)
gg.clearResults()
gg.toast("Hɪᴛ Eғғᴇᴄᴛ")
so=gg.getRangesList('libUE4.so')[1].start
py=0xDA9618
setvalue(so+py,16,0)
gg.clearResults()
gg.toast("Cʀᴏsʜᴀɪʀ")
so=gg.getRangesList('libUE4.so')[1].start
py=0xDA9058
setvalue(so+py,16,0)
so=gg.getRangesList('libUE4.so')[1].start
py=0x193B0EC
setvalue(so+py,16,0)
so=gg.getRangesList('libUE4.so')[1].start
py=0x3B21638
setvalue(so+py,16,0)
so=gg.getRangesList('libUE4.so')[1].start
py=0x2A2FC00
setvalue(so+py,16,8)
gg.clearResults()
gg.toast("Hᴇᴀᴅsʜᴏᴛ")
so = gg.getRangesList("libUE4.so")[1].start
py = 40574496
setvalue(so + py, 16, 290)
gg.clearResults()
gg.toast("Iᴘᴀɪᴅ Vɪᴇᴡ")
so=gg.getRangesList('libUE4.so')[1].start
py=0x29F04A0
setvalue(so+py,16,0)
gg.toast("Yᴇʟʟᴏ Bᴜʟʟᴇᴛ")
so=gg.getRangesList('libUE4.so')[1].start
py=0x28F1E50
setvalue(so+py,4,-1222130000)
gg.toast("Bʟᴀᴄᴋ Sᴋʏ")
gg.alert("👑Aʟʟ Bʀᴜᴛᴀʟ Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end
 
function ch5()
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("2015175168", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(6)
gg.editAll("0", gg.TYPE_FLOAT)
gg.clearResults()
gg.setRanges(gg.REGION_C_DATA)
gg.searchNumber("360;0.0001;1478828288", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("0.0001", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(100)
gg.editAll("9999", gg.TYPE_FLOAT)
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("1.6615354e35;-5.8048945e26:9", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("1.6615354e35", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(6)
gg.editAll("1.6615351e35", gg.TYPE_FLOAT)
gg.clearResults()
gg.getResults(1)
gg.searchNumber("10100400 ")
gg.searchNumber("10100400 ")
gg.getResults(10)
gg.editAll("1101004062",gg.TYPE_DWORD)
gg.clearResults()
gg.alert("👑Aɪᴍʙᴏᴛ Bʀᴜᴛᴀʟ Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end
 
function ch6()
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-1937954991146794979", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1, 0)
gg.getResults(5)
gg.editAll("-1937954991314567168", gg.TYPE_QWORD)
gg.clearResults()
gg.alert("👑Sᴄᴏᴘᴇ Esᴘ Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end
 
function ch7()
effect = gg.multiChoice({
"[👑Lᴀɢ Fɪx👑]",
"[👑Dᴀᴍᴀɢᴇ Fɪx👑]",
"[👑Sᴄᴏᴘᴇ Fɪx👑]",
"[👑Fʟᴀsʜ Oɴ👑]",
"[👑Fʟᴀsʜ Oғғ👑]",
"[👑Sʟᴏᴡᴍᴏᴛɪᴏɴ Oɴ👑]",
"[👑Sʟᴏᴡᴍᴏᴛɪᴏɴ Oғғ👑]",
"[ʙᴀᴄᴋ]",
 
}, nil,  "👑Vɪᴋᴀsʜ Hᴀᴄᴋᴇʀ👑")
 
if effect == nil then
else
if effect[1] == true then
l1()
end
if effect[2] == true then
l2()
end
if effect[3] == true then
l3()
end
if effect[4] == true then
l4()
end
if effect[5] == true then
l5()
end
if effect[6] == true then
l6()
end
if effect[7] == true then
l7()
end
 
end
XGCK = -1
end
 
function l1()
gg.clearResults()
  gg.setRanges(gg.REGION_ANONYMOUS)
  gg.searchNumber("4,890,205,508,990,664,704", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)
  gg.getResults(100)
  gg.editAll("4,890,205,509,012,684,800", gg.TYPE_QWORD)
  gg.clearResults()
  gg.setRanges(gg.REGION_ANONYMOUS)
  gg.searchNumber("1400;0.10000000149;1000;88;60;30", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
  gg.searchNumber("60", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
  gg.getResults(100)
  gg.editAll("-50", gg.TYPE_FLOAT)
gg.alert("👑Sᴛᴜᴄᴋ Fɪx Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end
 
function l2()
gg.clearResults()
gg.setRanges(gg.REGION_C_DATA | gg.REGION_CODE_APP)
gg.searchNumber("-298284466;-1.304566e23F", gg.TYPE_DWORD, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("-298284466", gg.TYPE_DWORD, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(99)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.alert("👑Dᴀᴍᴀɢᴇ Fɪx Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end
 
 
function l3()
gg.clearResults()
gg.setRanges(gg.REGION_ANONYMOUS)
gg.searchNumber("0.37999999523F;1.0F:6", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("0.37999999523", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
scope=gg.getResults(55)
gg.editAll("-12", gg.TYPE_FLOAT)
gg.clearResults()
gg.alert("👑Sᴄᴏᴘᴇ Fɪx Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end
 
function l4()
gg.clearResults()
gg.setRanges(gg.REGION_ANONYMOUS)
gg.searchNumber("4,525,216,907,414,147,695", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("4,525,216,907,473,673,257", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-1,328,550,408,728,725,571", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("-1,328,550,408,576,460,390", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-1296744149883614555", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("-1296744149264269342", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-1296744149883614555", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("-18289292828288282888/280", gg.TYPE_QWORD)
gg.clearResults()
gg.searchNumber("-1505254313802431360", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("-1505254313804899999", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-2188679037581846016", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResultsCount()
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-1585267064848315881", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(100)
gg.editAll("-1585267068834414550", gg.TYPE_QWORD)
gg.clearResults()
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-1,883,348,481,058,764,210", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("-1,883,348,481,058,764,210", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(100)
gg.editAll("-1,883,348,485,055,444,540", gg.TYPE_QWORD)
gg.alert("👑Fʟᴀsʜ Sᴘᴇᴇᴅ Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end
 
function l5()
gg.clearResults()
gg.setRanges(gg.REGION_ANONYMOUS)
gg.searchNumber("4,525,216,907,473,673,257", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("4,525,216,907,414,147,695", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-1,328,550,408,576,460,390", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("-1,328,550,408,728,725,571", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-1296744149264269342", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("-1296744149883614555", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-18289292828288282888/280", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("-1296744149883614555", gg.TYPE_QWORD)
gg.clearResults()
gg.searchNumber("-1505254313804899999", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("-1505254313802431360", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-2188679037581846016", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResultsCount()
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-1585267068834414550", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(100)
gg.editAll("-1585267064848315881", gg.TYPE_QWORD)
gg.clearResults()
gg.alert("👑Fʟᴀsʜ Sᴘᴇᴇᴅ Dᴇᴀᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end
 
function l6()
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("0.0001;0::16", 16,false,gg.SIGN_EQUAL,0, -1)
gg.searchNumber("0", 16,false,gg.SIGN_EQUAL,0, -1)
gg.getResults(200)
gg.editAll("5.6",16)
gg.clearResults()
gg.alert("👑Sʟᴏᴡᴍᴏᴛɪᴏɴ Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end
 
function l7()
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("5.6", 16,false,gg.SIGN_EQUAL,0, -1)
gg.searchNumber("0", 16,false,gg.SIGN_EQUAL,0, -1)
gg.getResults(200)
gg.editAll("0.0001;0::16",16)
gg.clearResults()
gg.alert("👑Sʟᴏᴡᴍᴏᴛɪᴏɴ Dᴇᴀᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end
 
function ch8()
gg.clearResults()
gg.setRanges(gg.REGION_ANONYMOUS)
gg.searchNumber("5006313939071729664",gg.TYPE_QWORD, false, gg.SIGN_EQUAL, -0, -1)
gg.getResults(30)
gg.editAll("5006313936970041344", gg.TYPE_QWORD)
gg.sleep(300)
gg.editAll("5006313939071729664", gg.TYPE_QWORD)
gg.clearResults()
gg.toast("👑Cᴀʀ Jᴜᴍᴘ Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end
 
function ch9()
gg.clearResults()
gg.setRanges(gg.REGION_ANONYMOUS)
gg.searchNumber('150.241295', gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(50)
gg.editAll('0.647058857;0.30000001192::5', gg.TYPE_FLOAT)
gg.clearResults()
gg.setRanges(gg.REGION_ANONYMOUS)
gg.searchNumber('75.241295', gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(50)
gg.editAll('0.72727274895;0.34377467632::5', gg.TYPE_FLOAT)
gg.clearResults()
gg.alert("👑Cᴀʀ Sᴘᴇᴇᴅ Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end
 
function ch10()
effect = gg.multiChoice({
"[👑Mɪᴄʀᴏ Sᴘᴇᴇᴅ Oɴ👑]",
"[👑Mɪᴄʀᴏ Sᴘᴇᴇᴅ Oғғ👑]",
"[ ʙᴀᴄᴋ ]",
 
}, nil,  "👑Vɪᴋᴀsʜ Hᴀᴄᴋᴇʀ👑")
 
if effect == nil then
else
if effect[1] == true then
m1()
end
if effect[2] == true then
m2()
end
 
end
XGCK = -1
end
 
function m1()
gg.clearResults()
gg.setRanges(gg.REGION_ANONYMOUS)
gg.searchNumber("1;1;1;0.0001;20;0.0005;0.4::50", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("1", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(500)
gg.editAll("1.123", gg.TYPE_FLOAT)
gg.clearResults()
gg.alert("👑Mɪᴄʀᴏ Sᴘᴇᴇᴅ Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end
 
function m2()
gg.clearResults()
gg.setRanges(gg.REGION_ANONYMOUS)
gg.searchNumber("1.123", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("1", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(500)
gg.editAll("1;1;1;0.0001;20;0.0005;0.4::50", gg.TYPE_FLOAT)
gg.clearResults()
gg.alert("👑Mɪᴄʀᴏ Sᴘᴇᴇᴅ Dᴇᴀᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end
 
function ch11()
print("❮▬▬▬✧✧✧✧▬▬▬❯\n[👑]sᴄʀɪᴘᴛ ➪ ᴠɪᴋᴀsʜ sɪɴɢʜ\n[👑]ɢᴀᴍᴇ ➪ ᴘᴜʙɢ ʟɪᴛᴇ\n[👑]ᴅᴍ ➪ @IɴᴅɪᴀɴHᴀᴄᴋᴇʀ98\n[👑]ᴅᴀᴛᴇ ➪ "..os.date("%d/%m/%Y").."\n❮▬▬▬✧✧✧✧▬▬▬❯")
gg.skipRestoreState()
gg.setVisible(true)
  os.exit()
end
while true do
  if gg.isVisible(true) then
    PUBGMH = 1
    gg.setVisible(false)
  end
  if PUBGMH == 1 then
    START()
  end
end

RAW Paste Data
gg.toast("■□□□□□□□□□𝟭𝟬%")
gg.sleep(200)
gg.toast("■■□□□□□□□□𝟮𝟬%")
gg.sleep(200)
gg.toast("■■■□□□□□□□𝟯𝟬%")
gg.sleep(200)
gg.toast("■■■■□□□□□□𝟰𝟬%")
gg.sleep(200)
gg.toast("■■■■■□□□□□𝟱𝟬%")
gg.sleep(200)
gg.toast("■■■■■■□□□□𝟲𝟬%")
gg.sleep(200)
gg.toast("■■■■■■■□□□𝟳𝟬%")
gg.sleep(200)
gg.toast("■■■■■■■■□□𝟴𝟬%")
gg.sleep(200)
gg.toast("■■■■■■■■■□𝟵𝟬%")
gg.sleep(200)
gg.toast("■■■■■■■■■■𝟭𝟬𝟬%")
gg.sleep(500)
function split(szFullString, szSeparator) local nFindStartIndex = 1 local nSplitIndex = 1 local nSplitArray = {} while true do local nFindLastIndex = string.find (szFullString, szSeparator, nFindStartIndex) if not nFindLastIndex then nSplitArray[nSplitIndex] = string.sub(szFullString, nFindStartIndex, string.len (szFullString)) break end nSplitArray[nSplitIndex] = string.sub (szFullString, nFindStartIndex, nFindLastIndex - 1) nFindStartIndex = nFindLastIndex + string.len (szSeparator) nSplitIndex = nSplitIndex + 1 end return nSplitArray end function xgxc(szpy, qmxg) for x = 1, #(qmxg) do xgpy = szpy + qmxg[x]["offset"] xglx = qmxg[x]["type"] xgsz = qmxg[x]["value"] xgdj = qmxg[x]["freeze"] if xgdj == nil or xgdj == "" then gg.setValues({[1] = {address = xgpy, flags = xglx, value = xgsz}}) else gg.addListItems({[1] = {address = xgpy, flags = xglx, freeze = xgdj, value = xgsz}}) end xgsl = xgsl + 1 xgjg = true end end function xqmnb(qmnb) gg.clearResults() gg.setRanges(qmnb[1]["memory"]) gg.searchNumber(qmnb[3]["value"], qmnb[3]["type"]) if gg.getResultCount() == 0 then gg.toast(qmnb[2]["name"] .. "开启失败") else gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) if gg.getResultCount() == 0 then gg.toast(qmnb[2]["name"] .. "开启失败") else sl = gg.getResults(999999) sz = gg.getResultCount() xgsl = 0 if sz > 999999 then sz = 999999 end for i = 1, sz do pdsz = true for v = 4, #(qmnb) do if pdsz == true then pysz = {} pysz[1] = {} pysz[1].address = sl[i].address + qmnb[v]["offset"] pysz[1].flags = qmnb[v]["type"] szpy = gg.getValues(pysz) pdpd = qmnb[v]["lv"] .. ";" .. szpy[1].value szpd = split(pdpd, ";") tzszpd = szpd[1] pyszpd = szpd[2] if tzszpd == pyszpd then pdjg = true pdsz = true else pdjg = false pdsz = false end end end if pdjg == true then szpy = sl[i].address xgxc(szpy, qmxg) end end if xgjg == true then gg.toast(qmnb[2]["name"] .. "开启成功，一共修改" .. xgsl .. "条数据") else gg.toast(qmnb[2]["name"] .. "未搜索到数据，开启失败") end end end end function SearchWrite(Search, Write, Type) gg.clearResults() gg.setVisible(false) gg.searchNumber(Search[1][1], Type) local count = gg.getResultCount() local result = gg.getResults(count) gg.clearResults() local data = {} local base = Search[1][2] if (count > 0) then for i, v in ipairs(result) do v.isUseful = true end for k=2, #Search do local tmp = {} local offset = Search[k][2] - base local num = Search[k][1] for i, v in ipairs(result) do tmp[#tmp+1] = {} tmp[#tmp].address = v.address + offset tmp[#tmp].flags = v.flags end tmp = gg.getValues(tmp) for i, v in ipairs(tmp) do if ( tostring(v.value) ~= tostring(num) ) then result[i].isUseful = false end end end for i, v in ipairs(result) do if (v.isUseful) then data[#data+1] = v.address end end if (#data > 0) then local t = {} local base = Search[1][2] for i=1, #data do for k, w in ipairs(Write) do offset = w[2] - base t[#t+1] = {} t[#t].address = data[i] + offset t[#t].flags = Type t[#t].value = w[1] if (w[3] == true) then local item = {} item[#item+1] = t[#t] item[#item].freeze = true gg.addListItems(item) end end end gg.setValues(t) gg.toast("开启成功，一共修改"..#t.."条数据") gg.addListItems(t) else gg.toast("未搜索到数据，开启失败", false) return false end else gg.toast("Not Found") return false end end
function split(szFullString, szSeparator) local nFindStartIndex = 1 local nSplitIndex = 1 local nSplitArray = {} while true do local nFindLastIndex = string.find(szFullString, szSeparator, nFindStartIndex) if not nFindLastIndex then nSplitArray[nSplitIndex] = string.sub(szFullString, nFindStartIndex, string.len(szFullString)) break end nSplitArray[nSplitIndex] = string.sub(szFullString, nFindStartIndex, nFindLastIndex - 1) nFindStartIndex = nFindLastIndex + string.len(szSeparator) nSplitIndex = nSplitIndex + 1 end return nSplitArray end function xgxc(szpy, qmxg) for x = 1, #(qmxg) do xgpy = szpy + qmxg[x]["offset"] xglx = qmxg[x]["type"] xgsz = qmxg[x]["value"] gg.setValues({[1] = {address = xgpy, flags = xglx, value = xgsz}}) xgsl = xgsl + 1 end end function xqmnb(qmnb) gg.clearResults() gg.setRanges(qmnb[1]["memory"]) gg.searchNumber(qmnb[3]["value"], qmnb[3]["type"]) if gg.getResultCount() == 0 then gg.toast(qmnb[2]["name"] .. "") else gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) if gg.getResultCount() == 0 then gg.toast(qmnb[2]["name"] .. "") else sl = gg.getResults(999999) sz = gg.getResultCount() xgsl = 0 if sz > 999999 then sz = 999999 end for i = 1, sz do pdsz = true for v = 4, #(qmnb) do if pdsz == true then pysz = {} pysz[1] = {} pysz[1].address = sl[i].address + qmnb[v]["offset"] pysz[1].flags = qmnb[v]["type"] szpy = gg.getValues(pysz) pdpd = qmnb[v]["lv"] .. ";" .. szpy[1].value szpd = split(pdpd, ";") tzszpd = szpd[1] pyszpd = szpd[2] if tzszpd == pyszpd then pdjg = true pdsz = true else pdjg = false pdsz = false end end end if pdjg == true then szpy = sl[i].address xgxc(szpy, qmxg) xgjg = true end end if xgjg == true then gg.toast(qmnb[2]["name"] .. "" .. xgsl .. "") else gg.toast(qmnb[2]["name"] .. "") end end end end
function setvalue(address,flags,value) local tt={} tt[1]={} tt[1].address=address tt[1].flags=flags tt[1].value=value gg.setValues(tt) end
function setvalue(address,flags,value) local tt={} tt[1]={} tt[1].address=address tt[1].flags=flags tt[1].value=value gg.setValues(tt) end
function PS() end
function setvalue(address,flags,value) PS('Modify address value (address, value type, value to be modified)') local tt={} tt[1]={} tt[1].address=address tt[1].flags=flags tt[1].value=value gg.setValues(tt) end
function split(szFullString, szSeparator) local nFindStartIndex = 1 local nSplitIndex = 1 local nSplitArray = {} while true do local nFindLastIndex = string.find(szFullString, szSeparator, nFindStartIndex) if not nFindLastIndex then nSplitArray[nSplitIndex] = string.sub(szFullString, nFindStartIndex, string.len(szFullString)) break end nSplitArray[nSplitIndex] = string.sub(szFullString, nFindStartIndex, nFindLastIndex - 1) nFindStartIndex = nFindLastIndex + string.len(szSeparator) nSplitIndex = nSplitIndex + 1 end return nSplitArray end function xgxc(szpy, qmxg) for x = 1, #(qmxg) do xgpy = szpy + qmxg[x]["offset"] xglx = qmxg[x]["type"] xgsz = qmxg[x]["value"] xgdj = qmxg[x]["freeze"] if xgdj == nil or xgdj == "" then gg.setValues({[1] = {address = xgpy, flags = xglx, value = xgsz}}) else gg.addListItems({[1] = {address = xgpy, flags = xglx, freeze = xgdj, value = xgsz}}) end xgsl = xgsl + 1 xgjg = true end end function xqmnb(qmnb) gg.clearResults() gg.setRanges(qmnb[1]["memory"]) gg.searchNumber(qmnb[3]["value"], qmnb[3]["type"]) if gg.getResultCount() == 0 then gg.toast(qmnb[2]["name"] .. "open失败") else gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) gg.refineNumber(qmnb[3]["value"], qmnb[3]["type"]) if gg.getResultCount() == 0 then gg.toast(qmnb[2]["name"] .. "open失败") else sl = gg.getResults(999999) sz = gg.getResultCount() xgsl = 0 if sz > 999999 then sz = 999999 end for i = 1, sz do pdsz = true for v = 4, #(qmnb) do if pdsz == true then pysz = {} pysz[1] = {} pysz[1].address = sl[i].address + qmnb[v]["offset"] pysz[1].flags = qmnb[v]["type"] szpy = gg.getValues(pysz) pdpd = qmnb[v]["lv"] .. ";" .. szpy[1].value szpd = split(pdpd, ";") tzszpd = szpd[1] pyszpd = szpd[2] if tzszpd == pyszpd then pdjg = true pdsz = true else pdjg = false pdsz = false end end end if pdjg == true then szpy = sl[i].address xgxc(szpy, qmxg) end end if xgjg == true then gg.toast(qmnb[2]["name"] .. "open,共修改" .. xgsl .. "条数据") else gg.toast(qmnb[2]["name"] .. "open失败") end end end end --@Saifu_hkc
function setvalue(address,flags,value) local tt={} tt[1]={} tt[1].address=address tt[1].flags=flags tt[1].value=value gg.setValues(tt) end
function readWrite(Search,Get,Type,Range,Name) gg["clearResults"]() gg["setRanges"](Range) gg["setVisible"](false) if Search[1][1]~=false then _G["gg"]["searchAddress"](Search[1][1],0xFFFFFFFF,Search[1][4] or Type,_G["gg"]["SIGN_EQUAL"],Search[1][5] or 1,Search[1][6] or -1) end gg["searchNumber"](Search[1][2],Search[1][4] or Type,false,_G["gg"]["SIGN_EQUAL"],Search[1][5] or 1,Search[1][6] or -1) local count=gg["getResultCount"]() local result=gg["getResults"](count) gg["clearResults"]() local data={} local base=Search[1][3] if (count > 0) then for i,v in ipairs(result) do v.isUseful=true end for k=2,#Search do local tmp={} local offset=Search[k][2] - base local num=Search[k][1] for i,v in ipairs(result) do tmp[#tmp+1]={} tmp[#tmp].address=v.address+offset tmp[#tmp].flags=Search[k][3] or Type end tmp=gg["getValues"](tmp) for i,v in ipairs(tmp) do if v.flags==16 or v.flags==64 then values=tostring(v.value):sub(1,6) num=tostring(num):sub(1,6) else values=v.value end if tostring(values)~=tostring(num) then result[i].isUseful=false end end end for i,v in ipairs(result) do if (v.isUseful) then data[#data+1]=v.address end end if (#data > 0) then local t,t_={},{} local base=Search[1][3] for i=1,#data do for k,w in ipairs(Get) do offset=w[2] - base if w[1]==false then t_[#t_+1]={} t_[#t_].address=data[i]+offset t_[#t_].flags=Type th_=(th_) and th_+1 or 1 else t[#t+1]={} t[#t].address=data[i]+offset t[#t].flags=w[3] or Type t[#t].value=w[1] tg_=(tg_) and tg_+1 or 1 if (w[4]==true) then local item={} item[#item+1]=t[#t] item[#item].freeze=w[4] gg["addListItems"](item) end end end end tg=(tg_) and "\n modify"..tg_.."data" or "" th=(th_) and "" or "" gg["setValues"](t) t_=gg["getValues"](t_) gg["loadResults"](t_) gg["toast"]("\n"..Name..tg) tg_,th_=nil,nil else gg["toast"]("Not searchable",false) return false end else gg["toast"]("Not searchable") return false end end

gg.alert("❮▬▬▬✧✧✧✧▬▬▬❯\n[👑]sᴄʀɪᴘᴛ ➪ ᴠɪᴋᴀsʜ sɪɴɢʜ\n[👑]ɢᴀᴍᴇ ➪ ᴘᴜʙɢ ʟɪᴛᴇ\n[👑]ᴅᴍ ➪ Vɪᴋᴀsʜ Hᴀᴄᴋᴇʀ\n[👑]ᴅᴀᴛᴇ ➪ "..os.date("%d/%m/%Y").."\n❮▬▬▬✧✧✧✧▬▬▬❯")

function START()
VG = gg.multiChoice({
"╔✧[👑]\n╚✧Bʏᴘᴀss Lᴏɢᴏ",  ---1
"╔✧[👑]\n╚✧Bʏᴘᴀss Lᴏʙʙʏ", ---2
"╔✧[👑]\n╚✧Bʟᴏᴄᴋ Rᴇᴘᴏʀᴛ", ---3
"╔✧[👑]\n╚✧Aʟʟ Bʀᴜᴛᴀʟ", ---4
"╔✧[👑]\n╚✧Aɪᴍʙᴏᴛ", ---5
"╔✧[👑]\n╚✧Sᴄᴏᴘᴇ Esᴘ",----6
"╔✧[👑]\n╚✧Fʟᴀsʜ Mᴇɴᴜ",----7
"╔✧[👑]\n╚✧Cᴀʀ Jᴜᴍᴘ",-----8
"╔✧[👑]\n╚✧Cᴀʀ Sᴘᴇᴇᴅ",----9
"╔✧[👑]\n╚✧Mɪᴄʀᴏ Sᴘᴇᴇᴅ",-----10
"╔✧[👑]\n╚✧Exɪᴛ Sᴄʀɪᴘᴛ",----11

}, nil, (os.date("❮▬▬▬✧✧✧✧▬▬▬❯\n[👑]sᴄʀɪᴘᴛ ➪ ᴠɪᴋᴀsʜ sɪɴɢʜ\n[👑]ɢᴀᴍᴇ ➪ ᴘᴜʙɢ ʟɪᴛᴇ\n[👑]ᴅᴍ ➪ Vɪᴋᴀsʜ Hᴀᴄᴋᴇʀ\n[👑]ᴅᴀᴛᴇ ➪ "..os.date("%d/%m/%Y").."\n❮▬▬▬✧✧✧✧▬▬▬❯")))


if VG == nil then else
if VG[1] == true then
ch1()
end
if VG[2] == true then
ch2()
end
if VG[3] == true then
ch3()
end
if VG[4] == true then
ch4()
end
if VG[5] == true then
ch5()
end
if VG[6] == true then
ch6()
end
if VG[7] == true then
ch7()
end
if VG[8] == true then
ch8()
end
if VG[9] == true then
ch9()
end
if VG[10] == true then
ch10()
end
if VG[11] == true then
ch11()
end

end
PUBGMH = -1
end


function ch1()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("620137442967552;564058054983680")
gg.refineNumber("620137442967552")
gg.getResults(50000)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("578351706144768;564058054983680")
gg.refineNumber("578351706144768")
gg.getResults(50000)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("577252194516992;564058054983680")
gg.refineNumber("577252194516992")
gg.getResults(50000)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("579451217772544;564058054983680")
gg.refineNumber("579451217772544;")
gg.getResults(50000)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber(":com.tencent.iglite.ztf", gg.TYPE_BYTE)
gg.getResults(50000)
gg.editAll("119", gg.TYPE_BYTE)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber(":com.tencent.iglite.ztf", gg.TYPE_BYTE)
gg.getResults(50000)
gg.editAll("119", gg.TYPE_BYTE)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("582749752655872;564058054983680")
gg.refineNumber("582749752655872;")
gg.getResults(50000)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("573953659633664;564058054983680")
gg.refineNumber("573953659633664")
gg.getResults(50000)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("582749752655872;564058054983680")
gg.refineNumber("582749752655872")
gg.getResults(50000)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.alert("👑Aʟʟ Tʜɪʀᴅ Pᴀʀᴛʏ Fɪxᴇᴅ Nᴏᴡ Gᴏ Lᴏʙʙʏ Aɴᴅ Aᴘᴘʟʏ Lᴏʙʙʏ Bʏᴘᴀss👑")
end

function ch2()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("620137442967552;564058054983680", gg.TYPE_QWORD)
gg.refineNumber("620137442967552", gg.TYPE_QWORD)
gg.getResults(50000)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("578351706144768;564058054983680", gg.TYPE_QWORD)
gg.refineNumber("578351706144768", gg.TYPE_QWORD)
gg.getResults(62877)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.searchNumber("577252194516992;564058054983680", gg.TYPE_QWORD)
gg.refineNumber("577252194516992", gg.TYPE_QWORD)
gg.getResults(50010)
gg.editAll("361418272522109953", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("909391408")
gg.getResults(62877)
gg.editAll("1089886885", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("909391408")
gg.getResults(999)
gg.editAll("1089886885", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("67633927;67109377")
gg.getResults(50000)
gg.editAll("67633927", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("67109390;67114093")
gg.getResults(50000)
gg.editAll("67633927", gg.TYPE_DWORD)
gg.clearResults()
gg.alert("👑Bʏᴘᴀss Lᴏʙʙʏ Aᴄᴛɪᴠᴀᴛᴇᴅ Nᴏᴡ Gᴏ Iᴄᴇʟᴀɴᴅ Aɴᴅ Aᴘʟʟʏ Rᴇᴘᴏʀᴛ Bʟᴏᴄᴋ Eᴠᴇʀʏ Mᴀᴛᴄʜ👑")
end

function ch3()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("524304", gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("29793", gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("41097", gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("34842", gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber('"2002204"',gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("459861", gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("925013", gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("19970", gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("786544", gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber("909391408", gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber('"3158585"',gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber('"2002006"',gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber('"3159606"',gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber('"2493002"',gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.setRanges(gg.REGION_C_ALLOC)
gg.searchNumber('"2001001"',gg.TYPE_DWORD)
gg.getResults(9999)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.alert("👑Rᴇᴘᴏʀᴛ Bʟᴏᴄᴋ Aᴄᴛɪᴠᴀᴛᴇᴅ Nᴏᴡ Sᴛᴀʀᴛ Aʟʟ Hᴀᴄᴋs Nᴏ Aɴʏ Bᴀɴ👑")
end

function ch4()
gg.clearResults()
so=gg.getRangesList('libUE4.so')[1].start
py=0x216F8F8
setvalue(so+py,16,0)
gg.toast("Dᴇsᴇʀᴛ Mᴀᴘ")
so=gg.getRangesList('libUE4.so')[1].start
py=0xDA9058
setvalue(so+py,16,0)
gg.toast("Lᴇss Rᴇᴄᴏɪʟ")
so = gg.getRangesList("libUE4.so")[1].start
py = 18242552
setvalue(so + py, 16, 0)
gg.clearResults()
gg.toast("Hɪᴛ Eғғᴇᴄᴛ")
so=gg.getRangesList('libUE4.so')[1].start
py=0xDA9618
setvalue(so+py,16,0)
gg.clearResults()
gg.toast("Cʀᴏsʜᴀɪʀ")
so=gg.getRangesList('libUE4.so')[1].start
py=0xDA9058
setvalue(so+py,16,0)
so=gg.getRangesList('libUE4.so')[1].start
py=0x193B0EC
setvalue(so+py,16,0)
so=gg.getRangesList('libUE4.so')[1].start
py=0x3B21638
setvalue(so+py,16,0)
so=gg.getRangesList('libUE4.so')[1].start
py=0x2A2FC00
setvalue(so+py,16,8)
gg.clearResults()
gg.toast("Hᴇᴀᴅsʜᴏᴛ")
so = gg.getRangesList("libUE4.so")[1].start
py = 40574496
setvalue(so + py, 16, 290)
gg.clearResults()
gg.toast("Iᴘᴀɪᴅ Vɪᴇᴡ")
so=gg.getRangesList('libUE4.so')[1].start
py=0x29F04A0
setvalue(so+py,16,0)
gg.toast("Yᴇʟʟᴏ Bᴜʟʟᴇᴛ")
so=gg.getRangesList('libUE4.so')[1].start
py=0x28F1E50
setvalue(so+py,4,-1222130000)
gg.toast("Bʟᴀᴄᴋ Sᴋʏ")
gg.alert("👑Aʟʟ Bʀᴜᴛᴀʟ Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end

function ch5()
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("2015175168", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(6)
gg.editAll("0", gg.TYPE_FLOAT)
gg.clearResults()
gg.setRanges(gg.REGION_C_DATA)
gg.searchNumber("360;0.0001;1478828288", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("0.0001", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(100)
gg.editAll("9999", gg.TYPE_FLOAT)
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("1.6615354e35;-5.8048945e26:9", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("1.6615354e35", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(6)
gg.editAll("1.6615351e35", gg.TYPE_FLOAT)
gg.clearResults()
gg.getResults(1)
gg.searchNumber("10100400 ")
gg.searchNumber("10100400 ")
gg.getResults(10)
gg.editAll("1101004062",gg.TYPE_DWORD)
gg.clearResults()
gg.alert("👑Aɪᴍʙᴏᴛ Bʀᴜᴛᴀʟ Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end

function ch6()
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-1937954991146794979", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1, 0)
gg.getResults(5)
gg.editAll("-1937954991314567168", gg.TYPE_QWORD)
gg.clearResults()
gg.alert("👑Sᴄᴏᴘᴇ Esᴘ Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end

function ch7()
effect = gg.multiChoice({
"[👑Lᴀɢ Fɪx👑]",
"[👑Dᴀᴍᴀɢᴇ Fɪx👑]",
"[👑Sᴄᴏᴘᴇ Fɪx👑]",
"[👑Fʟᴀsʜ Oɴ👑]",
"[👑Fʟᴀsʜ Oғғ👑]",
"[👑Sʟᴏᴡᴍᴏᴛɪᴏɴ Oɴ👑]",
"[👑Sʟᴏᴡᴍᴏᴛɪᴏɴ Oғғ👑]",
"[ʙᴀᴄᴋ]",

}, nil,  "👑Vɪᴋᴀsʜ Hᴀᴄᴋᴇʀ👑")

if effect == nil then
else
if effect[1] == true then
l1()
end
if effect[2] == true then
l2()
end
if effect[3] == true then
l3()
end
if effect[4] == true then
l4()
end
if effect[5] == true then
l5()
end
if effect[6] == true then
l6()
end
if effect[7] == true then
l7()
end

end
XGCK = -1
end

function l1()
gg.clearResults()
  gg.setRanges(gg.REGION_ANONYMOUS)
  gg.searchNumber("4,890,205,508,990,664,704", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)
  gg.getResults(100)
  gg.editAll("4,890,205,509,012,684,800", gg.TYPE_QWORD)
  gg.clearResults()
  gg.setRanges(gg.REGION_ANONYMOUS)
  gg.searchNumber("1400;0.10000000149;1000;88;60;30", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
  gg.searchNumber("60", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
  gg.getResults(100)
  gg.editAll("-50", gg.TYPE_FLOAT)
gg.alert("👑Sᴛᴜᴄᴋ Fɪx Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end

function l2()
gg.clearResults()
gg.setRanges(gg.REGION_C_DATA | gg.REGION_CODE_APP)
gg.searchNumber("-298284466;-1.304566e23F", gg.TYPE_DWORD, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("-298284466", gg.TYPE_DWORD, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(99)
gg.editAll("0", gg.TYPE_DWORD)
gg.clearResults()
gg.alert("👑Dᴀᴍᴀɢᴇ Fɪx Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end


function l3()
gg.clearResults()
gg.setRanges(gg.REGION_ANONYMOUS)
gg.searchNumber("0.37999999523F;1.0F:6", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("0.37999999523", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
scope=gg.getResults(55)
gg.editAll("-12", gg.TYPE_FLOAT)
gg.clearResults()
gg.alert("👑Sᴄᴏᴘᴇ Fɪx Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end

function l4()
gg.clearResults()
gg.setRanges(gg.REGION_ANONYMOUS)
gg.searchNumber("4,525,216,907,414,147,695", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("4,525,216,907,473,673,257", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-1,328,550,408,728,725,571", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("-1,328,550,408,576,460,390", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-1296744149883614555", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("-1296744149264269342", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-1296744149883614555", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("-18289292828288282888/280", gg.TYPE_QWORD)
gg.clearResults()
gg.searchNumber("-1505254313802431360", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("-1505254313804899999", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-2188679037581846016", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResultsCount()
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-1585267064848315881", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(100)
gg.editAll("-1585267068834414550", gg.TYPE_QWORD)
gg.clearResults()
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-1,883,348,481,058,764,210", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("-1,883,348,481,058,764,210", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(100)
gg.editAll("-1,883,348,485,055,444,540", gg.TYPE_QWORD)
gg.alert("👑Fʟᴀsʜ Sᴘᴇᴇᴅ Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end

function l5()
gg.clearResults()
gg.setRanges(gg.REGION_ANONYMOUS)
gg.searchNumber("4,525,216,907,473,673,257", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("4,525,216,907,414,147,695", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-1,328,550,408,576,460,390", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("-1,328,550,408,728,725,571", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-1296744149264269342", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("-1296744149883614555", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-18289292828288282888/280", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("-1296744149883614555", gg.TYPE_QWORD)
gg.clearResults()
gg.searchNumber("-1505254313804899999", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(1401)
gg.editAll("-1505254313802431360", gg.TYPE_QWORD)
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-2188679037581846016", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResultsCount()
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("-1585267068834414550", gg.TYPE_QWORD, false, gg.SIGN_EQUAL, 0, -1)  
gg.getResults(100)
gg.editAll("-1585267064848315881", gg.TYPE_QWORD)
gg.clearResults()
gg.alert("👑Fʟᴀsʜ Sᴘᴇᴇᴅ Dᴇᴀᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end

function l6()
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("0.0001;0::16", 16,false,gg.SIGN_EQUAL,0, -1)
gg.searchNumber("0", 16,false,gg.SIGN_EQUAL,0, -1)
gg.getResults(200)
gg.editAll("5.6",16)
gg.clearResults()
gg.alert("👑Sʟᴏᴡᴍᴏᴛɪᴏɴ Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end

function l7()
gg.clearResults()
gg.setRanges(gg.REGION_CODE_APP)
gg.searchNumber("5.6", 16,false,gg.SIGN_EQUAL,0, -1)
gg.searchNumber("0", 16,false,gg.SIGN_EQUAL,0, -1)
gg.getResults(200)
gg.editAll("0.0001;0::16",16)
gg.clearResults()
gg.alert("👑Sʟᴏᴡᴍᴏᴛɪᴏɴ Dᴇᴀᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end

function ch8()
gg.clearResults()
gg.setRanges(gg.REGION_ANONYMOUS)
gg.searchNumber("5006313939071729664",gg.TYPE_QWORD, false, gg.SIGN_EQUAL, -0, -1)
gg.getResults(30)
gg.editAll("5006313936970041344", gg.TYPE_QWORD)
gg.sleep(300)
gg.editAll("5006313939071729664", gg.TYPE_QWORD)
gg.clearResults()
gg.toast("👑Cᴀʀ Jᴜᴍᴘ Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end

function ch9()
gg.clearResults()
gg.setRanges(gg.REGION_ANONYMOUS)
gg.searchNumber('150.241295', gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(50)
gg.editAll('0.647058857;0.30000001192::5', gg.TYPE_FLOAT)
gg.clearResults()
gg.setRanges(gg.REGION_ANONYMOUS)
gg.searchNumber('75.241295', gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(50)
gg.editAll('0.72727274895;0.34377467632::5', gg.TYPE_FLOAT)
gg.clearResults()
gg.alert("👑Cᴀʀ Sᴘᴇᴇᴅ Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end

function ch10()
effect = gg.multiChoice({
"[👑Mɪᴄʀᴏ Sᴘᴇᴇᴅ Oɴ👑]",
"[👑Mɪᴄʀᴏ Sᴘᴇᴇᴅ Oғғ👑]",
"[ ʙᴀᴄᴋ ]",

}, nil,  "👑Vɪᴋᴀsʜ Hᴀᴄᴋᴇʀ👑")

if effect == nil then
else
if effect[1] == true then
m1()
end
if effect[2] == true then
m2()
end

end
XGCK = -1
end

function m1()
gg.clearResults()
gg.setRanges(gg.REGION_ANONYMOUS)
gg.searchNumber("1;1;1;0.0001;20;0.0005;0.4::50", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("1", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(500)
gg.editAll("1.123", gg.TYPE_FLOAT)
gg.clearResults()
gg.alert("👑Mɪᴄʀᴏ Sᴘᴇᴇᴅ Aᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end

function m2()
gg.clearResults()
gg.setRanges(gg.REGION_ANONYMOUS)
gg.searchNumber("1.123", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.searchNumber("1", gg.TYPE_FLOAT, false, gg.SIGN_EQUAL, 0, -1)
gg.getResults(500)
gg.editAll("1;1;1;0.0001;20;0.0005;0.4::50", gg.TYPE_FLOAT)
gg.clearResults()
gg.alert("👑Mɪᴄʀᴏ Sᴘᴇᴇᴅ Dᴇᴀᴄᴛɪᴠᴀᴛᴇᴅ Sᴜᴄᴄᴇsғᴜʟʟʏ👑")
end

function ch11()
print("❮▬▬▬✧✧✧✧▬▬▬❯\n[👑]sᴄʀɪᴘᴛ ➪ ᴠɪᴋᴀsʜ sɪɴɢʜ\n[👑]ɢᴀᴍᴇ ➪ ᴘᴜʙɢ ʟɪᴛᴇ\n[👑]ᴅᴍ ➪ @IɴᴅɪᴀɴHᴀᴄᴋᴇʀ98\n[👑]ᴅᴀᴛᴇ ➪ "..os.date("%d/%m/%Y").."\n❮▬▬▬✧✧✧✧▬▬▬❯")
gg.skipRestoreState()
gg.setVisible(true)
  os.exit()
end
while true do
  if gg.isVisible(true) then
    PUBGMH = 1
    gg.setVisible(false)
  end
  if PUBGMH == 1 then
    START()
  end
end
