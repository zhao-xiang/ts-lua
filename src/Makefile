.SUFFIXES: .c .o .lo

COMPILE = $(CC) -Wall -Wno-deprecated-declarations -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -g
INC_PATH = -Imodules -I/home/quehan/opt/master/include
LIB_PATH = -L/usr/local/lib -lssl -llua-5.1 -lpcre -ltcl

TS_LUA_SHARED_OBJS = \
	ts_lua.lo \
	ts_lua_string.lo \
	ts_lua_client_request.lo \
	ts_lua_client_response.lo \
	ts_lua_server_request.lo \
	ts_lua_server_response.lo \
	ts_lua_cached_response.lo \
	ts_lua_util.lo \
	ts_lua_remap.lo \
	ts_lua_hook.lo \
	ts_lua_context.lo \
	ts_lua_misc.lo \
	ts_lua_http.lo \
	ts_lua_transform.lo \
	ts_lua_log.lo \
	ts_lua_http_intercept.lo \
	ts_lua_regex.lo \
	ts_lua_http_config.lo \
	ts_lua_crypto.lo \
	ts_lua_hash_table.lo \
	ts_lua_mgmt.lo \
	ts_lua_http_cntl.lo \
	ts_lua_shared_dict.lo \
	ts_lua_package.lo \
	ts_lua_constant.lo \
	ts_lua_coroutine.lo \
	ts_lua_fetch.lo \
	ts_lua_io.lo \
	ts_lua_cache.lo

TS_LUA_LIB_SHARED_OBJS = \
	lib/ts_fetcher.lo

ALL_OBJS = $(TS_LUA_SHARED_OBJS) $(TS_LUA_LIB_SHARED_OBJS)

ALL_PRGS = 
ALL_LIBS = libtslua.so

all: $(ALL_OBJS) $(ALL_PRGS) $(ALL_LIBS)

libtslua.so:
	$(COMPILE) -o $@ $< -shared $(TS_LUA_SHARED_OBJS) $(TS_LUA_LIB_SHARED_OBJS) $(LIB_PATH)
.c:
	$(COMPILE) -o $@ $< $(TS_LUA_SHARED_OBJS) $(LIB_PATH) $(INC_PATH)
.c.o:
	$(COMPILE) -c -o $@ $<  $(INC_PATH)
.c.lo:
	$(COMPILE) -c -fPIC -o $@ $<  $(INC_PATH)
install:
	/bin/cp -f $(ALL_LIBS) /usr/lib64/trafficserver/plugins/
clean:
	rm -f $(ALL_OBJS) $(ALL_PRGS) $(ALL_LIBS)

