
prebuild:
	cd group && bldmake bldfiles gcce urel

build:
	cd group && abld build -v gcce urel


clean:
	cd group && abld reallyclean gcce urel


RENV_ADDR="10.42.0.231"
APP_NAME=cceleste
SIS_SRC="sis/$(APP_NAME)_gcce.sisx"
SIS_DST=`basename sis/$(APP_NAME)_gcce.sisx`
EXE=$(APP_NAME).exe
EXE_FP=$(EPOCROOT)/epoc32/release/gcce/urel/$(EXE)

mksis:
	cd sis && makesis -v -d$(EPOCROOT) $(APP_NAME)_gcce.pkg

mksisx:
	cd sis && signsis $(APP_NAME)_gcce.sis $(APP_NAME)_gcce.sisx mycert.cer mykey.key

depoly:
	renv -m c -s $(RENV_ADDR)  -c "sendfile $(SIS_SRC) /data/$(SIS_DST)"
run:
	renv -m c -s $(RENV_ADDR) -c "sendfile $(EXE_FP) D:\\$(EXE)"
	renv -m c -s $(RENV_ADDR) -c "copyfile D:\\$(EXE) C:\\sys\\bin\\$(EXE)"
	renv -m c -s $(RENV_ADDR) -c "runexe $(EXE) 0 1"

