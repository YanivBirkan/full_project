<script>
    invisibleColumnns = []

 

var columns2present = [
    {id:0,name:"ID",alias:"ID",isVisible:true},
    {id:1,name:"REFERENCE_ID",alias:"Reference Id",isVisible:false},
    {id:2,name:"CUSTOMER_NAME",alias:"Customer Name",isVisible:true},
    {id:3,name:"CUSTOMER_DESCRIPTION",alias:"Customer Description",isVisible:false},
    {id:4,name:"BILLING_ADDRESS",alias:"Billing Address",isVisible:true},
    {id:5,name:"PRIMARY_CONTACT",alias:"Primary Contact",isVisible:false},
    {id:6,name:"CUSTOMER_FIELD_C1",alias:"Cutomer Field C",isVisible:true},
    {id:7,name:"CUSTOMER_FIELD_C2",alias:"Cutomer Field C2",isVisible:false},
    {id:8,name:"CUSTOMER_FIELD_C3",alias:"Cutomer Field C3",isVisible:true},
    {id:9,name:"CUSTOMER_FIELD_C4",alias:"Cutomer Field C4",isVisible:false},
    {id:10,name:"CUSTOMER_FIELD_C5",alias:"Cutomer Field C5",isVisible:true},
    {id:11,name:"CUSTOMER_FIELD C6",alias:"Cutomer Field C6",isVisible:false},
    {id:12,name:"CUSTOMER_FIELD_C7",alias:"Cutomer Field C7",isVisible:false},
    {id:13,name:"CUSTOMER_FIELD_C8",alias:"Cutomer Field C8",isVisible:true},
    {id:14,name:"SIMS_COUNT",alias:"Sims Count",isVisible:false},
    {id:15,name:"ALLOCATED_SIMS",alias:"Allocated Sims",isVisible:true},
    {id:16,name:"ACTIVE_SIMS",alias:"Active Sims",isVisible:false},
    {id:17,name:"OBLIGO",alias:"Obligo ",isVisible:true},
    {id:18,name:"CURRENT_OBLIGO_BALLANCE",alias:"Current Oblligo Ballance",isVisible:true},
    {id:19,name:"buttons",alias:"Buttons",isVisible:true}

]


    let ColumnsAray = [] ;
    let RowsAray = [] ;
    let stringtitle =0;
    let RowData = [];
    let table2 =0;
    let table =0;
    let specid =0;
    let RowDataAray = [ ];
    let  columns = [];
    let  columns2 = [];
    let flag = 1;
    let lastrow = -1 ;
    let row =0;
    let ColumnsInvocieDetailsAray = [];
    let RowDetailsData = [];
    let RowDetailDataAray = [];

    $(document).ready(function() {
        $('.loading-overlay').show();
        loadAdminCustomers2();
        });
    function loadAdminCustomers2(){
        execGenericApi("GetCustomersList",[user_group_id],function(data){
            console.log(data);
            TableGetConfig(data);
            $('.loading-overlay').hide();
        });
    }

    function TableGetConfig(data){
        //push from the api aray the title to new ColumnsAray that will be used for data table
        columns2present.forEach(element=>{
            ColumnsAray.push(element.alias)
        });


        // //get and push the title for columns 
        // data.columnList.forEach(element => {
        //     let columntitle = element.replaceAll("_", " ");
        //     ColumnsAray.push(columntitle);       
        // });

        //create aray of the data for the row and push it to new RowsAray that will be used for data table
        data.data.forEach(element => {
            //push to Rowsaray(all the data of the specific row) - element in place ([]) column(name of the column)
            data.columnList.forEach(column => {
                RowsAray.push(  
                    element[column]  
                );
            });
            RowData.push(RowsAray); 
            RowsAray=[];          
        }); 
        //get  push the title for columns
        ColumnsAray.forEach((element)  => {  
            columns.push({title:element}); 
        });
        //get and push the data
        RowData.forEach(element =>{
            RowDataAray.push(element)
        });
        create_Dtable(columns , RowDataAray , "CustomersList");
        columnList = [];
        ColumnsAray=[];
        columns=[];
        RowDataAray=[];
        RowData=[];
}

function create_Dtable(columns , data , id ){
    let invisibleColumnns  =[];
    columns2present.forEach(element=>{
        if (element.isVisible==false) {
            invisibleColumnns.push(element.id);
            
        }
        
    });
    debugger
    //crerate the html
    $("#CustomerTable").append(" <div class='divtable'><table  class='display table table-striped table-bordered ' cellspacing='0' width='100%' height='1000px'></table> </div></div>");
    $(".divtable").children().attr('id' , id);
    //$(".dataTables_scrollBody").css('height' , '1000px');
    table = $('#' + id).DataTable( {
        searching: true,
        dom: "Bfrtip",
        columns: columns,
        data: data,
        //give id for the tr
        "fnCreatedRow": function( nRow, aData, iDataIndex ) {
            iDataIndex=0;
            $(nRow).attr('id', 'tr-' + iDataIndex);
            iDataIndex++;
        },
        paging: false,
        "columnDefs": [
            {
                "targets": invisibleColumnns,
                "visible": false,
                "searchable": false,

                
            },
            {
                "targets": -1,
                "defaultContent": "<div style='width: 500px' class='btn-group btn-group-toggle' data-toggle='buttons'><button class='btn btn-success'  id='test'>Button1</button> <button class='btn btn-primary' style='margin-left: 10px !important' id='test2' >Button2</button></div>"
            },

        ],
        buttons: [],
        fixedColumns: true
    });
    debugger
    console.log(invisibleColumnns);
    // var tbl = $('#CustomersList');
    // console.log(invisibleColumnns);
    // HideColumnAray.forEach(element=>{
    //     tbl.DataTable().columns(element.id).visible(element.visible); 
    // });
}

</script>
<section class="admin-page">
    <section class="top-admin-pages">
        <ol class="breadcrumbs">
            <li>
                <a onclick='loadSelectedPage("admin")'>Admin</a>
            </li>
            <li>
                <b>Customers2</b>
            </li>
        </ol>
    </section>
    <figure class="card">
        <main class="admin-topic-content customers" id="CustomerTable">
                
        </main>
    </figure>
</section>
