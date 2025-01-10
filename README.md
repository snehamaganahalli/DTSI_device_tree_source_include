# DTSI_device_tree_source_include

https://gist.github.com/robimarko/8a1bbb58dc6278d436c1aea52601c883

Below 
		dp1 {
			device_type = "network";
			compatible = "qcom,nss-dp";
			qcom,id = <0x01>;
			reg = <0x3a001000 0x200>;
			qcom,mactype = <0x00>;
			local-mac-address = [00 00 00 00 00 00];
			qcom,link-poll = <0x01>;
			qcom,phy-mdio-addr = <0x00>;
			phy-mode = "sgmii";
		};

  The above snippet is present in one of the dtsi file.
  id is the id of the device
  
  reg is the register address space of the device. 0x3a001000 is the start address and 0x200 is the length of the address space
  
  mactype represents which MAC type. It can be synopsis GMAC/QCOM GMAC etc...
  
  link-poll = <0x01> => the ethernet cable if we disconnect and connect then we get a print on the console. This is because link-poll is set to 1.

  mdio is media input output. It is the BUS on which GMAC sits.

  SGMII: Serial Gigabit Media Independent Interface
  MII: Media interface interconnect

==============================
EDMA: Enhanced DMA. Transfer of data from i/o to memory without involving CPU.

  		edma@3ab00000 {
			compatible = "qcom,edma";
			reg = <0x3ab00000 0x76900>;
			reg-names = "edma-reg-base";
			qcom,txdesc-ring-start = <0x17>;
			qcom,txdesc-rings = <0x01>;
			qcom,txcmpl-ring-start = <0x07>;
			qcom,txcmpl-rings = <0x01>;
			qcom,rxfill-ring-start = <0x07>;
			qcom,rxfill-rings = <0x01>;
			qcom,rxdesc-ring-start = <0x0f>;
			qcom,rxdesc-rings = <0x01>;
			interrupts = <0x00 0x159 0x04 0x00 0x161 0x04 0x00 0x169 0x04 0x00 0x158 0x04>;
			resets = <0x03 0x8a>;
			reset-names = "edma_rst";
		};
  ============
  nss firmware
  		nss@40000000 {
			compatible = "qcom,nss";
			interrupts = <0x00 0x179 0x01 0x00 0x17a 0x01 0x00 0x17b 0x01 0x00 0x17c 0x01 0x00 0x17d 0x01 0x00 0x17e 0x01 0x00 0x17f 0x01 0x00 0x180 0x01 0x00 0x181 0x01>;
			reg = <0x39000000 0x1000 0x38000000 0x30000 0xb111000 0x1000>;
			reg-names = "nphys\0vphys\0qgic-phys";
			clocks = <0x03 0x77 0x03 0x88 0x03 0x73 0x03 0x71 0x03 0x76 0x03 0x8e 0x03 0x6a 0x03 0xd9 0x03 0x8f 0x03 0x70 0x03 0x6f 0x03 0x8a 0x03 0x89 0x03 0x90 0x03 0x9a 0x03 0x98 0x03 0x99 0x03 0x9b 0x03 0xda>;
			clock-names = "nss-noc-clk\0nss-ptp-ref-clk\0nss-csr-clk\0nss-cfg-clk\0nss-imem-clk\0nss-nssnoc-qosgen-ref-clk\0nss-mem-noc-nss-axi-clk\0nss-nssnoc-snoc-clk\0nss-nssnoc-timeout-ref-clk\0nss-ce-axi-clk\0nss-ce-apb-clk\0nss-nssnoc-ce-axi-clk\0nss-nssnoc-ce-apb-clk\0nss-nssnoc-ahb-clk\0nss-core-clk\0nss-ahb-clk\0nss-axi-clk\0nss-mpt-clk\0nss-nc-axi-clk";
			qcom,id = <0x00>;
			qcom,num-queue = <0x04>;
			qcom,num-irq = <0x09>;
			qcom,num-pri = <0x04>;
			qcom,load-addr = <0x40000000>;
			qcom,low-frequency = "\v(r";
			qcom,mid-frequency = <0x2ca1c800>;
			qcom,max-frequency = <0x59439000>;
			qcom,bridge-enabled;
			qcom,ipv4-enabled;
			qcom,ipv4-reasm-enabled;
			qcom,ipv6-enabled;
			qcom,ipv6-reasm-enabled;
			qcom,wlanredirect-enabled;
			qcom,tun6rd-enabled;
			qcom,l2tpv2-enabled;
			qcom,gre-enabled;
			qcom,gre-redir-enabled;
			qcom,map-t-enabled;
			qcom,portid-enabled;
			qcom,ppe-enabled;
			qcom,pppoe-enabled;
			qcom,pptp-enabled;
			qcom,tunipip6-enabled;
			qcom,shaping-enabled;
			qcom,wlan-dataplane-offload-enabled;
			qcom,vlan-enabled;
			npu-supply = <0x18>;
			mx-supply = <0x18>;
		};
  
  =========
  
