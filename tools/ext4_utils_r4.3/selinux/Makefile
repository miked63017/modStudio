common_SRC_FILES := \
	src/booleans.c \
	src/canonicalize_context.c \
	src/disable.c \
	src/enabled.c \
	src/fgetfilecon.c \
	src/fsetfilecon.c \
	src/getenforce.c \
	src/getfilecon.c \
	src/getpeercon.c \
	src/lgetfilecon.c \
	src/load_policy.c \
	src/lsetfilecon.c \
	src/policyvers.c \
	src/procattr.c \
	src/setenforce.c \
	src/setfilecon.c \
	src/context.c \
	src/mapping.c \
	src/stringrep.c \
	src/compute_create.c \
	src/compute_av.c \
	src/avc.c \
	src/avc_internal.c \
	src/avc_sidtab.c \
	src/get_initial_context.c \
	src/checkAccess.c

common_HOST_FILES := \
	src/callbacks.c \
	src/check_context.c \
	src/freecon.c \
	src/init.c \
	src/label.c \
	src/label_file.c \
	src/label_android_property.c \
	src/android.c

common_SRC_FILES_obj := $(common_SRC_FILES:.c=.o)
common_HOST_FILES_obj := $(common_HOST_FILES:.c=.o)

TGT := libselinux.a

all: $(TGT)

%.o: %.c
	gcc -I. -I.. -DHOST -DANDROID -c $< -o $@

$(TGT): $(common_SRC_FILES_obj) $(common_HOST_FILES_obj)
	ar rvs $@ $^

.PHONY: clean clobber
clean:
	rm -f src/*.o 
clobber: clean
	rm -f $(TGT)
