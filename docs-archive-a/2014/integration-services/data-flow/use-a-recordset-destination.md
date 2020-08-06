---
title: 레코드 집합 대상 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Recordset destination
ms.assetid: a7b143dc-8008-404f-83b0-b45ffbca6029
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 34d1d5a7aa76876a9d8718b691b1d24a8835e2e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659541"
---
# <a name="use-a-recordset-destination"></a><span data-ttu-id="82a03-102">레코드 집합 대상 사용</span><span class="sxs-lookup"><span data-stu-id="82a03-102">Use a Recordset Destination</span></span>
  <span data-ttu-id="82a03-103">레코드 집합 대상은 외부 데이터 원본에 데이터를 저장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-103">The Recordset destination does not save data to an external data source.</span></span> <span data-ttu-id="82a03-104">대신 `Object` 데이터 형식의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지 변수에 저장된 레코드 집합의 데이터를 메모리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-104">Instead, the Recordset destination saves data in memory in a recordset that is stored in an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package variable of the `Object` data type.</span></span> <span data-ttu-id="82a03-105">레코드 집합 대상이 데이터를 저장한 후에는 일반적으로 Foreach 루프 컨테이너를 Foreach ADO 열거자와 함께 사용하여 레코드 집합의 행을 한 번에 하나씩 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-105">After the Recordset destination saves the data, you typically use a Foreach Loop container with the Foreach ADO enumerator to process one row of the recordset at a time.</span></span> <span data-ttu-id="82a03-106">Foreach ADO 열거자는 현재 행의 각 열 값을 개별 패키지 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-106">The Foreach ADO enumerator saves the value from each column of the current row into a separate package variable.</span></span> <span data-ttu-id="82a03-107">그러면 Foreach 루프 컨테이너 내에 구성한 태스크가 변수에서 이러한 값을 읽어 와서 이를 가지고 몇 가지 동작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-107">Then, the tasks that you configure inside the Foreach Loop container read those values from the variables and perform some action with them.</span></span>  
  
 <span data-ttu-id="82a03-108">레코드 집합 대상은 다양한 시나리오에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-108">You can use the Recordset destination in many different scenarios.</span></span> <span data-ttu-id="82a03-109">예를 들어 다음과 같은 노래를 선택할 수 있다.</span><span class="sxs-lookup"><span data-stu-id="82a03-109">Here are some examples:</span></span>  
  
-   <span data-ttu-id="82a03-110">메일 보내기 태스크와 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 식 언어를 사용하여 레코드 집합의 각 행에 대해 사용자 지정 전자 메일 메시지를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-110">You can use a Send Mail task and the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language to send a customized e-mail message for each row in the recordset.</span></span>  
  
-   <span data-ttu-id="82a03-111">데이터 흐름 태스크 내에서 원본으로 구성된 스크립트 구성 요소를 사용하여 열 값을 데이터 흐름의 열로 읽어올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-111">You can use a Script component configured as a source, inside a Data Flow task, to read the column values into the columns of the data flow.</span></span> <span data-ttu-id="82a03-112">그런 다음 변환 및 대상을 사용하여 행을 변환하고 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-112">Then, you can use transformations and destinations to transform and save the row.</span></span> <span data-ttu-id="82a03-113">이 예에서는 데이터 흐름 태스크가 각 행에 대해 한 번씩 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-113">In this example, the Data Flow task runs once for each row.</span></span>  
  
 <span data-ttu-id="82a03-114">다음 섹션에서는 먼저 레코드 집합 대상을 사용하는 일반적인 프로세스에 대해 설명한 다음 대상을 사용하는 방법에 대한 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-114">The following sections first describe the general process of using the Recordset destination and then show a specific example of how to use the destination.</span></span>  
  
## <a name="general-steps-to-using-a-recordset-destination"></a><span data-ttu-id="82a03-115">레코드 집합 대상을 사용하는 일반적인 단계</span><span class="sxs-lookup"><span data-stu-id="82a03-115">General Steps to Using a Recordset Destination</span></span>  
 <span data-ttu-id="82a03-116">다음 절차에서는 레코드 집합 대상에 데이터를 저장한 다음 Foreach 루프 컨테이너를 사용하여 각 행을 처리하는 데 필요한 단계를 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-116">The following procedure summarizes the steps that are required to save data to a Recordset destination, and then use the Foreach Loop container to process each row.</span></span>  
  
#### <a name="to-save-data-to-a-recordset-destination-and-process-each-row-by-using-the-foreach-loop-container"></a><span data-ttu-id="82a03-117">레코드 집합 대상에 데이터를 저장하고 Foreach 루프 컨테이너를 사용하여 각 행을 처리하려면</span><span class="sxs-lookup"><span data-stu-id="82a03-117">To save data to a Recordset destination and process each row by using the Foreach Loop container</span></span>  
  
1.  <span data-ttu-id="82a03-118">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 만들거나 엽니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-118">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], create or open an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>  
  
2.  <span data-ttu-id="82a03-119">레코드 집합 대상이 메모리에 저장한 레코드 집합을 보유할 변수를 만든 다음 이 변수의 유형을 `Object`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-119">Create a variable that will contain the recordset saved into memory by the Recordset destination, and set the variable's type to `Object`.</span></span>  
  
3.  <span data-ttu-id="82a03-120">사용할 레코드 집합의 각 열 값을 보유할 적절한 유형의 추가 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-120">Create additional variables of the appropriate types to contain the values of each column in the recordset that you want to use.</span></span>  
  
4.  <span data-ttu-id="82a03-121">데이터 흐름에서 사용할 데이터 원본에 필요한 연결 관리자를 추가하고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-121">Add and configure the connection manager required by the data source that you plan to use in your data flow.</span></span>  
  
5.  <span data-ttu-id="82a03-122">패키지에 데이터 흐름 태스크를 추가하고 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너의 데이터 흐름 탭에서 데이터를 로드하고 변환할 원본과 변환을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-122">Add a Data Flow task to the package, and on the Data Flow tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, configure sources and transformations to load and transform the data.</span></span>  
  
6.  <span data-ttu-id="82a03-123">데이터 집합 대상을 데이터 흐름에 추가하고 이를 변환에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-123">Add a Recordset destination to the data flow and connect it to the transformations.</span></span> <span data-ttu-id="82a03-124">레코드 집합 대상의 `VariableName` 속성에 대해 레코드 집합을 보유하기 위해 만든 변수의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-124">For the `VariableName` property of the Recordset destination, enter the name of the variable that you created to hold the recordset.</span></span>  
  
7.  <span data-ttu-id="82a03-125">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너의 제어 흐름 탭에서 Foreach 루프 컨테이너를 추가하고 이 컨테이너를 데이터 흐름 태스크 뒤에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-125">On the Control Flow tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add a Foreach Loop container and connect this container after the Data Flow task.</span></span> <span data-ttu-id="82a03-126">그런 다음 **Foreach 루프 편집기** 를 열어 다음과 같이 컨테이너를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-126">Then, open the **Foreach Loop Editor** to configure the container with the following settings:</span></span>  
  
    1.  <span data-ttu-id="82a03-127">**컬렉션** 페이지에서 Foreach ADO 열거자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-127">On the **Collection** page, select the Foreach ADO Enumerator.</span></span> <span data-ttu-id="82a03-128">그런 다음 **ADO 개체 원본 변수**에 대해 레코드 집합이 들어 있는 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-128">Then, for **ADO object source variable**, select the variable that contains the recordset.</span></span>  
  
    2.  <span data-ttu-id="82a03-129">**변수 매핑** 페이지에서 사용할 각 열의 0부터 시작하는 인덱스를 적절한 변수에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-129">On the **Variable Mappings** page, map the zero-based index of each column that you want to use to the appropriate variable.</span></span>  
  
         <span data-ttu-id="82a03-130">루프가 반복될 때마다 열거자는 현재 행의 열 값으로 이러한 변수를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-130">On each iteration of the loop, the enumerator populates these variables with the column values from the current row.</span></span>  
  
8.  <span data-ttu-id="82a03-131">Foreach 루프 컨테이너 내에서 변수의 값을 읽어 와서 레코드 집합의 행을 한 번에 하나씩 처리하는 태스크를 추가하고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-131">Inside the Foreach Loop container, add and configure tasks to process one row of the recordset at a time by reading the values from the variables.</span></span>  
  
## <a name="example-of-using-the-recordset-destination"></a><span data-ttu-id="82a03-132">레코드 집합 대상을 사용하는 예</span><span class="sxs-lookup"><span data-stu-id="82a03-132">Example of Using the Recordset Destination</span></span>  
 <span data-ttu-id="82a03-133">다음 예에서는 데이터 흐름 태스크가 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 직원에 대한 정보를 Sales.SalesPerson 테이블에서 레코드 집합 대상으로 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-133">In the following example, the Data Flow task loads information about [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] employees from the Sales.SalesPerson table into a Recordset destination.</span></span> <span data-ttu-id="82a03-134">그러면 Foreach 루프 컨테이너에서 데이터 행을 한 번에 하나씩 읽고 메일 보내기 태스크를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-134">Then, a Foreach Loop container reads one row of data at a time, and calls a Send Mail task.</span></span> <span data-ttu-id="82a03-135">메일 보내기 태스크는 식을 사용하여 보너스 금액에 관한 사용자 지정 전자 메일 메시지를 각 판매 직원에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-135">The Send Mail task uses expressions to send a customized e-mail message to each salesperson about the amount of his or her bonus.</span></span>  
  
#### <a name="to-create-the-project-and-configure-the-variables"></a><span data-ttu-id="82a03-136">프로젝트를 만들고 변수를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="82a03-136">To create the project and configure the variables</span></span>  
  
1.  <span data-ttu-id="82a03-137">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 새 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-137">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="82a03-138">**SSIS** 메뉴에서 **변수**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-138">On the **SSIS** menu, select **Variables**.</span></span>  
  
3.  <span data-ttu-id="82a03-139">**변수** 창에서 다음과 같이 레코드 집합과 현재 행의 열 값을 보유할 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-139">In the **Variables** window, create the variables that will hold the recordset and the column values from the current row:</span></span>  
  
    1.  <span data-ttu-id="82a03-140">`BonusRecordset`이라는 변수를 만들고 이 변수의 유형을 `Object`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-140">Create a variable named, `BonusRecordset`, and set its type to `Object`.</span></span>  
  
         <span data-ttu-id="82a03-141">`BonusRecordset` 변수는 레코드 집합을 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-141">The `BonusRecordset` variable holds the recordset.</span></span>  
  
    2.  <span data-ttu-id="82a03-142">`EmailAddress`이라는 변수를 만들고 이 변수의 유형을 `String`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-142">Create a variable named, `EmailAddress`, and set its type to `String`.</span></span>  
  
         <span data-ttu-id="82a03-143">`EmailAddress` 변수는 판매 직원의 전자 메일 메시지를 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-143">The `EmailAddress` variable holds the salesperson's e-mail address.</span></span>  
  
    3.  <span data-ttu-id="82a03-144">`FirstName`이라는 변수를 만들고 이 변수의 유형을 `String`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-144">Create a variable named, `FirstName`, and set its type to `String`.</span></span>  
  
         <span data-ttu-id="82a03-145">`FirstName` 변수는 판매 직원의 이름을 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-145">The `FirstName` variable holds the salesperson's first name.</span></span>  
  
    4.  <span data-ttu-id="82a03-146">`Bonus`이라는 변수를 만들고 이 변수의 유형을 `Double`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-146">Create a variable named, `Bonus`, and set its type to `Double`.</span></span>  
  
         <span data-ttu-id="82a03-147">`Bonus` 변수는 판매 직원의 보너스를 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-147">The `Bonus` variable holds the amount of the salesperson's bonus.</span></span>  
  
#### <a name="to-configure-the-connection-managers"></a><span data-ttu-id="82a03-148">연결 관리자를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="82a03-148">To configure the connection managers</span></span>  
  
1.  <span data-ttu-id="82a03-149">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너의 연결 관리자 영역에서 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 예제 데이터베이스에 연결하는 새 OLE DB 연결 관리자를 추가하고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-149">In the Connection Managers area of the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add and configure a new OLE DB connection manager that connects to the [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sample database.</span></span>  
  
     <span data-ttu-id="82a03-150">데이터 흐름 태스크의 OLE DB 원본은 이 연결 관리자를 사용하여 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-150">The OLE DB source in the Data Flow task will use this connection manager to retrieve data.</span></span>  
  
2.  <span data-ttu-id="82a03-151">연결 관리자 영역에서 사용 가능한 SMTP 서버에 연결하는 새 SMTP 연결 관리자를 추가하고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-151">In the Connection Managers area, add and configure a new SMTP connection manager that connects to an available SMTP server.</span></span>  
  
     <span data-ttu-id="82a03-152">Foreach 루프 컨테이너 내의 메일 보내기 태스크는 이 연결 관리자를 사용하여 전자 메일을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-152">The Send Mail task inside the Foreach Loop container will use this connection manager to send emails.</span></span>  
  
#### <a name="to-configure-the-data-flow-and-the-recordset-destination"></a><span data-ttu-id="82a03-153">데이터 흐름 및 레코드 집합 대상을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="82a03-153">To configure the data flow and the Recordset Destination</span></span>  
  
1.  <span data-ttu-id="82a03-154">**디자이너의** 제어 흐름 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 탭에서 디자인 화면에 데이터 흐름 태스크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-154">On the **Control Flow** tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add a Data Flow task to the design surface.</span></span>  
  
2.  <span data-ttu-id="82a03-155">**데이터 흐름** tab, add an OLE DB source to the 데이터 흐름 task, and then open the **OLE DB 원본 편집기**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-155">On the **Data Flow** tab, add an OLE DB source to the Data Flow task, and then open the **OLE DB Source Editor.**</span></span>  
  
3.  <span data-ttu-id="82a03-156">OLE DB 원본 편집기의 **연결 관리자** 페이지에서 다음과 같이 원본을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-156">On the **Connection Manager** page of the editor, configure the source with the following settings:</span></span>  
  
    1.  <span data-ttu-id="82a03-157">**OLE DB 연결 관리자**에 대해 이전에 만든 OLE DB 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-157">For **OLE DB connection manager**, select the OLE DB connection manager that you previously created.</span></span>  
  
    2.  <span data-ttu-id="82a03-158">**데이터 액세스 모드**에 대해 **SQL 명령**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-158">For **Data access mode**, select **SQL command**.</span></span>  
  
    3.  <span data-ttu-id="82a03-159">**SQL 명령 텍스트**에 대해 다음 쿼리를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-159">For **SQL command text**, enter the following query:</span></span>  
  
        ```  
        SELECT     Person.Contact.EmailAddress, Person.Contact.FirstName, CONVERT(float, Sales.SalesPerson.Bonus) AS Bonus  
        FROM         Sales.SalesPerson INNER JOIN  
                              Person.Contact ON Sales.SalesPerson.SalesPersonID = Person.Contact.ContactID  
        ```  
  
        > [!NOTE]  
        >  <span data-ttu-id="82a03-160">Bonus 열의 `currency` 값을 `float` 유형의 패키지 변수에 로드하려면 먼저 이 값을 `Double`로 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-160">You have to convert the `currency` value in the Bonus column to a `float` before you can load that value into a package variable whose type is `Double`.</span></span>  
  
4.  <span data-ttu-id="82a03-161">**데이터 흐름** 탭에서 레코드 집합 대상을 추가하고 이 대상을 OLE DB 원본 뒤에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-161">On the **Data Flow** tab, add a Recordset destination, and connect the destination after the OLE DB source.</span></span>  
  
5.  <span data-ttu-id="82a03-162">**레코드 집합 대상 편집기**를 열고 다음과 같이 대상을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-162">Open the **Recordset Destination Editor**, and configure the destination with the following settings:</span></span>  
  
    1.  <span data-ttu-id="82a03-163">**구성 요소 속성** 탭에서 속성에 대해 `VariableName` 를 선택 `User::BonusRecordset` 합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-163">On the **Component Properties** tab, for `VariableName` property, select `User::BonusRecordset`.</span></span>  
  
    2.  <span data-ttu-id="82a03-164">**입력 열** 탭에서 사용 가능한 열 세 개를 모두 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-164">On the **Input Columns** tab, select all three of the available columns.</span></span>  
  
#### <a name="to-configure-the-foreach-loop-container-and-run-the-package"></a><span data-ttu-id="82a03-165">Foreach 루프 컨테이너를 구성하고 패키지를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="82a03-165">To configure the Foreach Loop container and run the package</span></span>  
  
1.  <span data-ttu-id="82a03-166">**디자이너의** 제어 흐름 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 탭에서 Foreach 루프 컨테이너를 추가하고 이 컨테이너를 데이터 흐름 태스크 뒤에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-166">On the **Control Flow** tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add a Foreach Loop container, and connect the container after the Data Flow task.</span></span>  
  
2.  <span data-ttu-id="82a03-167">**Foreach 루프 편집기**를 열고 다음과 같이 컨테이너를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-167">Open the **Foreach Loop Editor**, and configure the container with the following settings:</span></span>  
  
    1.  <span data-ttu-id="82a03-168">**컬렉션** 페이지에서 **열거자**에 대해 **Foreach ado 열거자**를 선택 하 고 **ADO 개체 원본 변수**에 대해를 선택 `User::BonusRecordset` 합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-168">On the **Collection** page, for **Enumerator**, select **Foreach ADO Enumerator**, and for **ADO object source variable**, select `User::BonusRecordset`.</span></span>  
  
    2.  <span data-ttu-id="82a03-169">**변수 매핑** 페이지에서 인덱스 `User::EmailAddress` 0, 인덱스 `User::FirstName` 1 및 `User::Bonus` 인덱스 2로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-169">On the **Variable Mappings** page, map `User::EmailAddress` to index 0, `User::FirstName` to index 1, and `User::Bonus` to index 2.</span></span>  
  
3.  <span data-ttu-id="82a03-170">**제어 흐름** 탭에서 Foreach 루프 컨테이너 내에 메일 보내기 태스크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-170">On the **Control Flow** tab, inside the Foreach Loop container, add a Send Mail task.</span></span>  
  
4.  <span data-ttu-id="82a03-171">**메일 보내기 태스크 편집기**를 열고 **메일** 페이지에서 다음과 같이 태스크를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-171">Open the **Send Mail Task Editor**, and then on the **Mail** page, configure the task with the following settings:</span></span>  
  
    1.  <span data-ttu-id="82a03-172">**SmtpConnection**에 대해 이전에 구성한 SMTP 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-172">For **SmtpConnection**, select the SMTP connection manager that was configured previously.</span></span>  
  
    2.  <span data-ttu-id="82a03-173">**보낸 사람**에 대해 적절한 전자 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-173">For **From**, enter an appropriate e-mail address.</span></span>  
  
         <span data-ttu-id="82a03-174">자신의 전자 메일 주소를 사용하면 패키지가 성공적으로 실행되는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-174">If you use your own e-mail address, you will be able to confirm that the package runs successfully.</span></span> <span data-ttu-id="82a03-175">메일 보내기 태스크를 통해 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]의 가상 판매 직원에게 메시지를 보내면 해당 수신인에게 메시지를 배달할 수 없다는 내용의 메시지가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-175">You will receive undeliverable receipts for the messages sent by the Send Mail task to the fictitious salespersons of [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].</span></span>  
  
    3.  <span data-ttu-id="82a03-176">**받는 사람**에 대해 기본 전자 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-176">For **To**, enter a default e-mail address.</span></span>  
  
         <span data-ttu-id="82a03-177">이 값은 사용되지 않지만 런타임에 각 판매 직원의 전자 메일 주소로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-177">This value will not be used, but will be replaced at run time by the e-mail address of each salesperson.</span></span>  
  
    4.  <span data-ttu-id="82a03-178">**제목**에 대해 "연간 보너스 안내"를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-178">For **Subject**, enter "Your annual bonus".</span></span>  
  
    5.  <span data-ttu-id="82a03-179">**MessageSourceType**에 대해 **직접 입력**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-179">For **MessageSourceType**, select **Direct Input**.</span></span>  
  
5.  <span data-ttu-id="82a03-180">**메일 보내기 태스크 편집기** 의 **식**페이지에서 줄임표 단추( **...** )를 클릭하여 **속성 식 편집기**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-180">On the **Expressions** page of the **Send Mail Task Editor**, click the ellipsis button (**...**) to open the **Property Expressions Editor**.</span></span>  
  
6.  <span data-ttu-id="82a03-181">**속성 식 편집기**에서 다음 정보를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-181">In the **Property Expressions Editor**, enter the following information:</span></span>  
  
    1.  <span data-ttu-id="82a03-182">**ToLine**에 대해 다음 식을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-182">For **ToLine**, add the following expression:</span></span>  
  
        ```  
        @[User::EmailAddress]  
        ```  
  
    2.  <span data-ttu-id="82a03-183">**MessageSource** 속성에 대해 다음 식을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-183">For the **MessageSource** property, add the following expression:</span></span>  
  
        ```  
        "Dear " +  @[User::FirstName] + ": The amount of your bonus for this year is $" +  (DT_WSTR, 12) @[User::Bonus] + ". Thank you!"  
        ```  
  
7.  <span data-ttu-id="82a03-184">패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-184">Run the package.</span></span>  
  
     <span data-ttu-id="82a03-185">올바른 SMTP 서버를 지정하고 자신의 전자 메일 주소를 입력한 경우 메일 보내기 태스크를 통해 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]의 가상 판매 직원에게 메시지를 보내면 해당 수신인에게 메시지를 배달할 수 없다는 내용의 메시지가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="82a03-185">If you have specified a valid SMTP server and provided your own e-mail address, you will receive undeliverable receipts for the messages that the Send Mail task sends to the fictitious salespersons of [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].</span></span>  
  
  
