#CXX    := aarch64-linux-android21-clang++
#CC     := aarch64-linux-android21-clang
CXX    := /home/node/Android/Sdk/ndk/21.3.6528147/toolchains/llvm/prebuilt/linux-x86_64/bin/clang++
CC     := /home/node/Android/Sdk/ndk/21.3.6528147/toolchains/llvm/prebuilt/linux-x86_64/bin/clang
CFLAGS := -target aarch64-linux-android21 -O2 -Wall -fPIC
NAME=libimbe_vocoder.a
INSTALL_PATH=/usr/local/lib
INCLUDE_PATH=/usr/local/include

OBJECTS = aux_sub.o ch_encode.o dsp_sub.o imbe_vocoder_impl.o pitch_est.o rand_gen.o sa_enh.o v_synt.o \
          basicop2.o dc_rmv.o encode.o math_sub.o pitch_ref.o sa_decode.o tbls.o v_uv_det.o ch_decode.o \
          decode.o imbe_vocoder.o pe_lpf.o qnt_sub.o sa_encode.o uv_synt.o

.PHONY: all
all:		$(NAME)

$(NAME):	$(OBJECTS)
		$(AR) rcs $(NAME) $(OBJECTS)

-include $(OBJECTS:.o=.d)

%.o: %.cc
		$(CXX) $(CFLAGS) -c -o $@ $<
		$(CXX) -MM $(CFLAGS) $< > $*.d

.PHONY: clean
clean:
		$(RM) $(NAME) *.o *.d *.bak *~

install:
	cp $(NAME) $(INSTALL_PATH)
	cp imbe_vocoder_api.h $(INCLUDE_PATH)
