local memFrom, memTo, lib, num, lim, results, src, ok = 0, -1, nil, 0, 32, {}, nil, false
function name(n)
	if lib ~= n then
		lib = n
		local ranges = gg.getRangesList(lib)
		if #ranges == 0 then
			print("Error "..lib.."Arquivo do jogo Não encontrado")
			gg.toast("Error : "..lib.."Arquivo do jogo Não encontrado")
           gg.alert("Arquivo do jogo Não encontrado","SAIR")
			os.exit()
		else
			memFrom = ranges[1].start
			memTo = ranges[#ranges]["end"]
		end
	end
end
function hex2tbl(hex)
	local ret = {}
	hex:gsub("%S%S", function (ch)
		ret[#ret + 1] = ch
		return ""
	end)
	return ret
end
function original(orig)
	local tbl = hex2tbl(orig)
	local len = #tbl
	if len == 0 then return end
	local used = len
	if len > lim then used = lim end
	local s = ''
	for i = 1, used do
		if i ~= 1 then s = s..";" end
		local v = tbl[i]
		if v == "??" or v == "**" then v = "0~~0" end		
		s = s..v.."r"
	end
	s = s.."::"..used
	gg.searchNumber(s, gg.TYPE_BYTE, false, gg.SIGN_EQUAL, memFrom, memTo)
	if len > used then
		for i = used + 1, len do
			local v = tbl[i]
			if v == "??" or v == "**" then
				v = 256
			else
				v = ("0x"..v) + 0
				if v > 127 then v = v - 256 end
			end
			tbl[i] = v
		end
	end
	local found = gg.getResultCount();
	results = {}
	local count = 0
	local checked = 0
	while true do
		if checked >= found then
			break
		end
		local all = gg.getResults(8)
		local total = #all
		local start = checked
		if checked + used > total then
			break
		end
		for i, v in ipairs(all) do
	    v.address = v.address + myoffset
        end
         gg.loadResults(all)
		while start < total do		
			local good = true
			local offset = all[1 + start].address - 1
			if used < len then			
				local get = {}
				for i = lim + 1, len do
					get[i - lim] = {address = offset + i, flags = gg.TYPE_BYTE, value = 0}
				end
				get = gg.getValues(get)
				for i = lim + 1, len do
					local ch = tbl[i]
					if ch ~= 256 and get[i - lim].value ~= ch then
						good = false
						break
					end
				end
			end
			if good then
				count = count + 1
				results[count] = offset
				checked = checked + used
			else
				local del = {}
				for i = 1, used do
					del[i] = all[i + start]
				end
				gg.removeResults(del)
			end
			start = start + used
		end
	end
	
end
function replaced(repl)
	num = num + 1
	local tbl = hex2tbl(repl)
	if src ~= nil then
		local source = hex2tbl(src)
		for i, v in ipairs(tbl) do
			if v ~= "??" and v ~= "**" and v == source[i] then tbl[i] = "**" end
		end
		src = nil
	end
	local cnt = #tbl
	local set = {}
	local s = 0
	for _, addr in ipairs(results) do
		for i, v in ipairs(tbl) do
			if v ~= "??" and v ~= "**" then
				s = s + 1
				set[s] = {
					["address"] = addr + i, 
					["value"] = v.."r",
					["flags"] = gg.TYPE_BYTE,
				}
			end
		end		
	end
	if s ~= 0 then gg.setValues(set) end
	ok = true
end



function START()
menu = gg.choice({
'Shell Device',
'Shell Device 2',
'❌Closed'},nil,'Script By CoRinga BR')
if menu == 1 then A()end
if menu == 2 then B()end
if menu == 3 then os.exit()end
MPG = -1
end

function A()
menu1 = gg.multiChoice({
'🔓Unlock Device',
'❌Exit'},nil,'Script By CoRinga BR')
if menu1 == nil then else
if menu1[1] == true then A1()end
if menu1[2] == true then START()end
end
MPG = -1
end

function A1()
replaced = gg.prompt({"Unbanned Device v1"},nil,{"Text"})
gg.loadList(gg.EXT_STORAGE .. "/lib.hack", gg.LOAD_APPEND)
    gg.loadResults((gg.getListItems()))
    gg.removeListItems((gg.getListItems()))
    gg.setRanges(gg.REGION_CODE_APP | gg.REGION_C_DATA)
    name("libil2cpp.so")
    myoffset = 0x1590D04
    original("7F 45 4C 46 01 01 01 00")
    replaced("00 00 00 E3 1E FF 2F E1")
    gg.clearResults()
    gg.setRanges(gg.REGION_CODE_APP | gg.REGION_C_DATA)
    name("libil2cpp.so")
    myoffset = 0x1588BF0
    original("7F 45 4C 46 01 01 01 00")
    replaced("00 00 00 E3 1E FF 2F E1")
    gg.clearResults()
gg.setRanges(16392)
gg.searchNumber("-1.3093038e25;-1.3068388e21;-9.3858979e22;-9.4006553e22;-8.2433888e19;-7.6092819e19;-1.2278246e23;-3.8369228e21::29", 16, false, 536870912, 0, -1)
gg.searchNumber("-1.3093038e25;-1.3068388e21", 16, false, 536870912, 0, -1)
gg.getResults(7)
gg.editAll("-5.9029581e21;-2.0291021e20", 16)
gg.clearResults()
gg.setRanges(16392)
gg.searchNumber("-1.3093038e25;-1.3068388e21;-9.3858979e22;-9.4006553e22;-8.2433888e19;-7.6092819e19;-1.2278237e23;-3.8369228e21::29", 16, false, 536870912, 0, -1)
gg.searchNumber("-1.3093038e25;-1.3068388e21", 16, false, 536870912, 0, -1)
gg.getResults(7)
gg.editAll("-5.9029581e21;-2.0291021e20", 16)
gg.clearResults()
gg.setRanges(16392)
gg.searchNumber("-1.3093038e25;-1.3068388e21;-9.3858979e22;-9.4006553e22;-8.2433888e19;-7.6092819e19;-1.227824e23;-3.8369228e21::29", 16, false, 536870912, 0, -1)
gg.searchNumber("-1.3093038e25;-1.3068388e21", 16, false, 536870912, 0, -1)
gg.getResults(7)
gg.editAll("-5.9029581e21;-2.0291021e20", 16)
gg.clearResults()
gg.setRanges(16392)
gg.searchNumber("-1.3093038e25;-1.3068388e21;-9.3858979e22;-9.4006553e22;-8.2433888e19;-7.6092819e19;-1.2278243e23;-3.8369228e21::29", 16, false, 536870912, 0, -1)
gg.searchNumber("-1.3093038e25;-1.3068388e21", 16, false, 536870912, 0, -1)
gg.getResults(7)
gg.editAll("-5.9029581e21;-2.0291021e20", 16)
gg.clearResults()
gg.setRanges(16392)
gg.searchNumber("-1.3093038e25;-1.3068388e21;-9.3858979e22;-9.4006553e22;-8.2433888e19;-7.6092819e19;-1.2278245e23;-3.8369228e21::29", 16, false, 536870912, 0, -1)
gg.searchNumber("-1.3093038e25;-1.3068388e21", 16, false, 536870912, 0, -1)
gg.getResults(7)
gg.editAll("-5.9029581e21;-2.0291021e20", 16)
gg.clearResults()
gg.setRanges(16384)
gg.searchNumber("-1.3093038e25;-1.3068388e21;-9.3858979e22;-9.4006553e22::13", 16, false, 536870912, 0, -1)
gg.searchNumber("9.3858979e22", 16, false, 536870912, 0, -1)
gg.getResults(100)
gg.editAll("-5112e21", 16)
gg.clearResults()
gg.toast('Unlock Device By Mr•EzCheats')
end

function B()
menu1 = gg.multiChoice({
'🔓Unlock Shell',
'❌Exit'},nil,'Script By CoRinga BR')
if menu1 == nil then else
if menu1[1] == true then B1()end
if menu1[2] == true then START()end
end
MPG = -1
end


function B1()
replaced = gg.prompt({"Unbanned Device v2"},nil,{"Text"})
gg.loadList(gg.EXT_STORAGE .. "/lib.hack", gg.LOAD_APPEND)
    gg.loadResults((gg.getListItems()))
    gg.removeListItems((gg.getListItems()))
    gg.setRanges(gg.REGION_CODE_APP | gg.REGION_C_DATA)
    name("libil2cpp.so")
    myoffset = 0x1592FF4
    original("7F 45 4C 46 01 01 01 00")
    replaced("00 00 00 E3 1E FF 2F E1")
    gg.clearResults()
gg.toast('Desbloqueado')
end


while(true)do if gg.isVisible(true)then MPG = 1 gg.setVisible(false)end
if MPG == 1 then START()end
end








