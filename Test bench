module spi_ttb();
    parameter a_width=8,d_width=16;
    reg clk,rst,start,r_w;
    reg [d_width-1:0]w_data;
    reg [a_width-1:0]w_addr,r_addr;
    wire [d_width-1:0]r_data;
    wire sclk_w,cs_w,sdio_w;
    
    spi_t dut(clk,rst,start,r_w,w_addr,w_data,r_addr,r_data,sclk_w,cs_w,sdio_w);
    
    always #5 clk=~clk;
    
    initial begin
        {clk,start,w_data,w_addr,r_addr}=0;
        {rst}=1;
        #10 rst=0;
        start=1;
             r_w=0;
                w_addr='hfd;
                w_data='hfdfd;
/*       #500 r_w=1;
                r_addr='haa;
        #200 r_w=0;*/
        #500
                w_addr='hfe;
                w_data='hfefe;
        #500 
                w_addr='hab;
                w_data='habab;
        #500 r_w=1;
                r_addr='hab;
        #500 //r_w=1;
                r_addr='hfe;
        #500 
                r_addr='hfd;
                        
        #1000 $finish;
    
    end
    
    initial $monitor("time= %0d,clk= %0xb,rst= %0xb,start= %0xb,r_w= %0xb,w_addr= %0xh,w_data= %0xh,r_addr= %0xh,r_data= %0xh,sclk_w= %0xb,cs_w= %0xb,sdio_w= %0xb"
                     ,$time,clk,rst,start,r_w,w_addr,w_data,r_addr,r_data,sclk_w,cs_w,sdio_w);

endmodule
