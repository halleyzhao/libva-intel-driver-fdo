INTEL_PP_G8B = \
	pl2_to_pl2.g8b		\
	pl2_to_pl3.g8b		\
	pl3_to_pl2.g8b		\
	pl3_to_pl3.g8b		\
	pl2_to_rgbx.g8b		\
	rgbx_to_nv12.g8b	\
	pl2_to_pa.g8b		\
	pl3_to_pa.g8b		\
	pa_to_pl2.g8b		\
	pa_to_pl3.g8b		\
	pa_to_pa.g8b		\
	$(NULL)

INTEL_PP_G8A = \
	EOT.g8a				\
	PL2_AVS_Buf_0.g8a		\
	PL2_AVS_Buf_1.g8a		\
	PL2_AVS_Buf_2.g8a		\
	PL2_AVS_Buf_3.g8a		\
	PL3_AVS_Buf_0.g8a		\
	PL3_AVS_Buf_1.g8a		\
	PL3_AVS_Buf_2.g8a		\
	PL3_AVS_Buf_3.g8a		\
	PA_AVS_Buf_0.g8a		\
	PA_AVS_Buf_1.g8a		\
	PA_AVS_Buf_2.g8a		\
	PA_AVS_Buf_3.g8a		\
	Save_AVS_NV12.g8a		\
	Save_AVS_PL3.g8a		\
	Save_AVS_RGBX.g8a		\
	Save_AVS_PA.g8a			\
	Set_AVS_Buf_0123_PL2.g8a	\
	Set_AVS_Buf_0123_PL3.g8a	\
	Set_AVS_Buf_0123_BGRA.g8a	\
	Set_AVS_Buf_0123_VYUA.g8a	\
	YUV_to_RGB.g8a			\
	RGB_to_YUV.g8a			\
	Set_Layer_0.g8a			\
	VP_Setup.g8a			\
	$(NULL)

INTEL_PP_ASM = $(INTEL_PP_G8B:%.g8b=%.asm)
INTEL_PP_GEN8_ASM = $(INTEL_PP_G8B:%.g8b=%.g8s)

TARGETS  =
if HAVE_GEN4ASM
TARGETS += $(INTEL_PP_G8B)
endif

all-local: $(TARGETS)

SUFFIXES = .g8b .g8s .asm

$(INTEL_PP_GEN8_ASM): $(INTEL_PP_ASM) $(INTEL_PP_G8A)
.asm.g8s:
	$(AM_V_GEN)cpp $< > _pp0.$@;		\
	../../gpp.py _pp0.$@ $@;	\
	rm _pp0.$@
.g8s.g8b:
	$(AM_V_GEN)intel-gen4asm -a -o $@ -g 8 $<

CLEANFILES = $(INTEL_PP_GEN7_ASM)

EXTRA_DIST = \
	$(INTEL_PP_G8B)

# Extra clean files so that maintainer-clean removes *everything*
MAINTAINERCLEANFILES = Makefile.in
