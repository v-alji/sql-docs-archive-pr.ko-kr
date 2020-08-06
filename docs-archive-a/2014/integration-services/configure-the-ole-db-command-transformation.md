---
title: OLE DB 명령 변환 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- parameters [Integration Services]
- OLE DB Command transformation
ms.assetid: c800f167-3d2e-4c10-8ba3-a02f1872ccea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d1714a6b798c6d8256052fd3c16bd86182480bcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738632"
---
# <a name="configure-the-ole-db-command-transformation"></a><span data-ttu-id="73aa8-102">OLE DB 명령 변환 구성</span><span class="sxs-lookup"><span data-stu-id="73aa8-102">Configure the OLE DB Command Transformation</span></span>
  <span data-ttu-id="73aa8-103">OLE DB 명령 변환을 추가 및 구성하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크와 플랫 파일 원본이나 OLE DB 원본과 같은 원본이 이미 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-103">To add and configure an OLE DB Command transformation, the package must already include at least one Data Flow task and a source such as a Flat File source or an OLE DB source.</span></span> <span data-ttu-id="73aa8-104">이러한 변환은 일반적으로 매개 변수가 있는 쿼리에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-104">This transformation is typically used for running parameterized queries.</span></span>  
  
### <a name="to-configure-the-ole-db-command-transformation"></a><span data-ttu-id="73aa8-105">OLE DB 명령 변환을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="73aa8-105">To configure the OLE DB Command transformation</span></span>  
  
1.  <span data-ttu-id="73aa8-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="73aa8-107">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-107">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="73aa8-108">**데이터 흐름** 탭을 클릭한 다음 **도구 상자**에서 OLE DB 명령 변환을 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-108">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the OLE DB Command transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="73aa8-109">데이터 원본이나 이전 변환에서 연결선(녹색 또는 빨간색 화살표)을 OLE DB 명령 변환으로 끌어서 OLE DB 명령 변환을 데이터 흐름에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-109">Connect the OLE DB Command transformation to the data flow by dragging a connector-the green or red arrow-from a data source or a previous transformation to the OLE DB Command transformation.</span></span>  
  
5.  <span data-ttu-id="73aa8-110">구성 요소를 마우스 오른쪽 단추로 클릭하고 편집 또는 **고급 편집기 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-110">Right-click the component and select Edit or Show **Advanced Editor**.</span></span>  
  
6.  <span data-ttu-id="73aa8-111">**연결 관리자** 탭의 **연결 관리자** 목록에서 OLE DB 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-111">On the **Connection Managers** tab, select an OLE DB connection manager in the **Connection Manager** list.</span></span> <span data-ttu-id="73aa8-112">자세한 내용은 [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73aa8-112">For more information, see [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md).</span></span>  
  
7.  <span data-ttu-id="73aa8-113">**구성 요소 속성** 탭을 클릭하고 **SqlCommand** 상자의 줄임표 단추 **(...)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-113">Click the **Component Properties** tab and click the ellipsis button **(...)** in the **SqlCommand** box.</span></span>  
  
8.  <span data-ttu-id="73aa8-114">**문자열 값 편집기**에서 각 매개 변수에 대한 매개 변수 표시자로 물음표(?)를 사용하여 매개 변수가 있는 SQL 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-114">In the **String Value Editor**, type the parameterized SQL statement using a question mark (?) as the parameter marker for each parameter.</span></span>  
  
9. <span data-ttu-id="73aa8-115">**새로 고침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-115">Click **Refresh**.</span></span> <span data-ttu-id="73aa8-116">**새로 고침**을 클릭하면 변환이 외부 열 컬렉션의 각 매개 변수에 대한 열을 만들고 DBParamInfoFlags 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-116">When you click **Refresh**, the transformation creates a column for each parameter in the External Columns collection and sets the DBParamInfoFlags property.</span></span>  
  
10. <span data-ttu-id="73aa8-117">**입/출력 속성** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-117">Click the **Input and Output Properties** tab.</span></span>  
  
11. <span data-ttu-id="73aa8-118">**OLE DB 명령 입력**을 확장한 후 **외부 열**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-118">Expand **OLE DB Command Input**, and then expand **External Columns**.</span></span>  
  
12. <span data-ttu-id="73aa8-119">**외부 열** 목록에 SQL 문의 각 매개 변수에 대한 열이 나열되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-119">Verify that **External Columns** lists a column for each parameter in the SQL statement.</span></span> <span data-ttu-id="73aa8-120">열 이름은 **Param_0**, **Param_1**등입니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-120">The column names are **Param_0**, **Param_1**, and so on.</span></span>  
  
     <span data-ttu-id="73aa8-121">열 이름은 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-121">You should not change the column names.</span></span> <span data-ttu-id="73aa8-122">열 이름을 변경하면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 OLE DB 명령 변환에 대한 유효성 검사 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-122">If you change the column names, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a validation error for the OLE DB Command transformation.</span></span>  
  
     <span data-ttu-id="73aa8-123">데이터 형식도 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-123">Also, you should not change the data type.</span></span> <span data-ttu-id="73aa8-124">각 열의 DataType 속성은 올바른 데이터 형식으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-124">The DataType property of each column is set to the correct data type.</span></span>  
  
13. <span data-ttu-id="73aa8-125">**외부 열** 에 열이 나열되지 않으면 열을 수동으로 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-125">If **External Columns** lists no columns you must add them manually.</span></span>  
  
    -   <span data-ttu-id="73aa8-126">SQL 문의 각 매개 변수에 대해 **열 추가** 를 한 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-126">Click **Add Column** one time for each parameter in the SQL statement.</span></span>  
  
    -   <span data-ttu-id="73aa8-127">열 이름을 **Param_0**, **Param_1**등으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-127">Update the column names to **Param_0**, **Param_1**, and so on.</span></span>  
  
    -   <span data-ttu-id="73aa8-128">DBParamInfoFlags 속성에 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-128">Specify a value in the DBParamInfoFlags property.</span></span> <span data-ttu-id="73aa8-129">값은 OLE DB DBPARAMFLAGSENUM 열거의 값과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-129">The value must match a value in the OLE DB DBPARAMFLAGSENUM enumeration.</span></span> <span data-ttu-id="73aa8-130">자세한 내용은 OLE DB 참조 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="73aa8-130">For more information, see the OLE DB reference documentation.</span></span>  
  
    -   <span data-ttu-id="73aa8-131">열의 데이터 형식을 지정하고 데이터 형식에 따라 열의 코드 페이지, 길이, 전체 자릿수 및 소수 자릿수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-131">Specify the data type of the column and, depending on the data type, specify the code page, length, precision, and scale of the column.</span></span>  
  
    -   <span data-ttu-id="73aa8-132">사용되지 않는 매개 변수를 삭제하려면 **외부 열**에서 매개 변수를 선택한 후 **열 제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-132">To delete an unused parameter, select the parameter in **External Columns**, and then click **Remove Column**.</span></span>  
  
    -   <span data-ttu-id="73aa8-133">**열 매핑** 을 클릭하고 **사용 가능한 입력 열** 목록에 있는 열을 **사용 가능한 대상 열** 목록에 있는 매개 변수로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-133">Click **Column Mappings** and map columns in the **Available Input Columns** list to parameters in the **Available Destination Columns** list.</span></span>  
  
14. <span data-ttu-id="73aa8-134">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-134">Click **OK**.</span></span>  
  
15. <span data-ttu-id="73aa8-135">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73aa8-135">To save the updated package, click **Save** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73aa8-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73aa8-136">See Also</span></span>  
 <span data-ttu-id="73aa8-137">[명령 변환 OLE DB](data-flow/transformations/ole-db-command-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="73aa8-137">[OLE DB Command Transformation](data-flow/transformations/ole-db-command-transformation.md) </span></span>  
 <span data-ttu-id="73aa8-138">[Integration Services 변환](data-flow/transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="73aa8-138">[Integration Services Transformations](data-flow/transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="73aa8-139">[Integration Services 경로](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="73aa8-139">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 [<span data-ttu-id="73aa8-140">데이터 흐름 태스크</span><span class="sxs-lookup"><span data-stu-id="73aa8-140">Data Flow Task</span></span>](control-flow/data-flow-task.md)  
  
  
