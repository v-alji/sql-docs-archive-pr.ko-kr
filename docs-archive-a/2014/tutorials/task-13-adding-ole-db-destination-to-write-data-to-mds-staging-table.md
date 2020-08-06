---
title: '작업 13: MDS 준비 테이블에 데이터를 쓸 OLE DB 대상 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: e6c67fa9-bb52-44a9-82f6-d86551cf12b2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 77799782518a3be2441b4c461467e3132781298d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731191"
---
# <a name="task-13-adding-ole-db-destination-to-write-data-to-mds-staging-table"></a><span data-ttu-id="2e51a-102">태스크 13: OLE DB 대상을 추가하여 MDS 준비 테이블에 데이터 쓰기</span><span class="sxs-lookup"><span data-stu-id="2e51a-102">Task 13: Adding OLE DB Destination to Write Data to MDS Staging Table</span></span>
  <span data-ttu-id="2e51a-103">이제 모든 레코드에 **Importtype** 및 **batchtag** 값을 추가 했으므로 준비를 위해 MDS로 전송할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2e51a-103">Now that you have added **ImportType** and **BatchTag** values to all records, you are ready to send them over to MDS for staging.</span></span> <span data-ttu-id="2e51a-104">이 태스크에서는 OLE DB 대상을 사용 하 여 데이터를 **stg. supplier_Leaf** 준비 테이블에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e51a-104">In this task, you use the OLE DB Destination to write the data into **stg.supplier_Leaf** staging table.</span></span>  
  
1.  <span data-ttu-id="2e51a-105">**SSIS 도구 상자** 의 **다른 대상** 섹션에서 **데이터 흐름** 탭으로 **OLE DB Destination** 을 끌어서 **MDS에 필요한 열 추가**아래에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="2e51a-105">Drag **OLE DB Destination** from **Other Destinations** section in the **SSIS Toolbox** to the **Data Flow** tab and drop it under **Add Columns Required by MDS**.</span></span>  
  
2.  <span data-ttu-id="2e51a-106">**데이터 흐름** 탭에서 **대상 OLE DB** 를 마우스 오른쪽 단추로 클릭 하 고 **이름 바꾸기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e51a-106">Right-click **OLE DB Destination** in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="2e51a-107">**MDS 준비 테이블에 공급자 데이터 쓰기를** 입력 하 고 **enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="2e51a-107">Type **Write Supplier Data to MDS Staging Table** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="2e51a-108">파란색 커넥터를 사용 하 여 mds **준비 테이블에 공급자 데이터를 기록** 하는 **데 필요한 추가 열을 mds** 에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e51a-108">Connect the **Add Columns Required by MDS** to **Write Supplier Data to MDS Staging Table** using the blue connector.</span></span>  
  
4.  <span data-ttu-id="2e51a-109">**데이터 흐름** 탭에서 **MDS 준비 테이블에 공급자 데이터 쓰기를** 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e51a-109">Double-click **Write Supplier Data to MDS Staging Table** in the **Data Flow** tab.</span></span>  
  
5.  <span data-ttu-id="2e51a-110">**OLE DB 대상 편집기** 대화 상자에서 **(로컬)이 있는지 확인 합니다. MDS** (또는 **localhost) MDS**) **OLE DB 연결 관리자** 필드에 대해 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e51a-110">In the **OLE DB Destination Editor** Dialog box, make sure that **(local).MDS** (or **localhost.MDS**) is selected for the **OLE DB Connection Manager** field.</span></span>  
  
6.  <span data-ttu-id="2e51a-111">\*\*Stg를 선택 합니다. \*\* **테이블 또는 뷰의 이름**목록에서 테이블을 Supplier_Leaf 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e51a-111">Select **stg.Supplier_Leaf** table from the list of **Name of the table or the view**.</span></span>  
  
     <span data-ttu-id="2e51a-112">![OLEDB 대상 편집기](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-01.jpg "OLEDB 대상 편집기")</span><span class="sxs-lookup"><span data-stu-id="2e51a-112">![OLEDB Destination Editor](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-01.jpg "OLEDB Destination Editor")</span></span>  
  
7.  <span data-ttu-id="2e51a-113">왼쪽의 메뉴에서 **매핑** 을 클릭 하 여 **매핑** 페이지로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e51a-113">Switch to the **Mappings** page by clicking **Mapping** on the menu on left.</span></span>  
  
8.  <span data-ttu-id="2e51a-114">다음 표와 같이 **입력** 및 **대상** 열을 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="2e51a-114">Map **input** and **destination** columns as shown in the following table.</span></span>  
  
     <span data-ttu-id="2e51a-115">![OLEDB 대상 편집기 - 매핑](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-02.jpg "OLEDB 대상 편집기 - 매핑")</span><span class="sxs-lookup"><span data-stu-id="2e51a-115">![OLEDB Destination Editor - Mappings](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-02.jpg "OLEDB Destination Editor - Mappings")</span></span>  
  
9. <span data-ttu-id="2e51a-116">**_Status** 또는 **_Source** 열이 아닌 입력 열에 **_Output** 열을 사용 하 고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e51a-116">Confirm that you are using **_Output** columns for Input Columns, not the **_Status** or **_Source** columns.</span></span> <span data-ttu-id="2e51a-117">**_Output** 열에는 dqs 정리의 출력 값이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e51a-117">**_Output** columns contain the output values from DQS Cleansing.</span></span>  
  
10. <span data-ttu-id="2e51a-118">**확인** 을 클릭 하 여 **대상 편집기 OLE DB** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="2e51a-118">Click **OK** to close the **OLE DB Destination Editor** dialog box.</span></span>  
  
11. <span data-ttu-id="2e51a-119">데이터 흐름은 다음 이미지와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2e51a-119">The data flow should like the following image.</span></span>  
  
     <span data-ttu-id="2e51a-120">![완료된 데이터 흐름](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-03.jpg "완료된 데이터 흐름")</span><span class="sxs-lookup"><span data-stu-id="2e51a-120">![Completed Data Flow](../../2014/tutorials/media/et-addingoledbdestinationtowdtomdsst-03.jpg "Completed Data Flow")</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="2e51a-121">다음 단계</span><span class="sxs-lookup"><span data-stu-id="2e51a-121">Next Step</span></span>  
 [<span data-ttu-id="2e51a-122">태스크 14: Control Flow에 SQL 실행 태스크를 추가하여 MDS에 대한 저장 프로시저 실행</span><span class="sxs-lookup"><span data-stu-id="2e51a-122">Task 14: Adding Execute SQL Task to Control Flow to Run the Stored Procedure for MDS</span></span>](../../2014/tutorials/task-14-add-execute-to-control-flow-run-mds-stored-procedure.md)  
  
  
