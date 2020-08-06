---
title: OLE DB 명령 변환 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbcommandtrans.f1
helpviewer_keywords:
- statements [Integration Services]
- OLE DB Command transformation
ms.assetid: baa6735c-5acf-4759-b077-1216aca16c6c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a6b0498d0ae5fa61a00cc7f6fc89e4dc506cd25a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743428"
---
# <a name="ole-db-command-transformation"></a><span data-ttu-id="b97f2-102">OLE DB 명령 변환</span><span class="sxs-lookup"><span data-stu-id="b97f2-102">OLE DB Command Transformation</span></span>
  <span data-ttu-id="b97f2-103">OLE DB 명령 변환은 데이터 흐름의 각 행에 대해 SQL 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-103">The OLE DB Command transformation runs an SQL statement for each row in a data flow.</span></span> <span data-ttu-id="b97f2-104">예를 들어 데이터베이스 테이블에서 행을 삽입, 업데이트 또는 삭제하는 SQL 문을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-104">For example, you can run an SQL statement that inserts, updates, or deletes rows in a database table.</span></span>  
  
 <span data-ttu-id="b97f2-105">다음과 같은 방법으로 OLE DB 명령 변환을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-105">You can configure the OLE DB Command Transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="b97f2-106">각 행에 대해 변환을 실행하는 SQL 문을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-106">Provide the SQL statement that the transformation runs for each row.</span></span>  
  
-   <span data-ttu-id="b97f2-107">SQL 문이 시간 초과될 때까지 걸리는 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-107">Specify the number of seconds before the SQL statement times out.</span></span>  
  
-   <span data-ttu-id="b97f2-108">기본 코드 페이지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-108">Specify the default code page.</span></span>  
  
 <span data-ttu-id="b97f2-109">일반적으로 SQL 문에는 매개 변수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-109">Typically, the SQL statement includes parameters.</span></span> <span data-ttu-id="b97f2-110">매개 변수 값이 변환 입력의 외부 열에 저장되고 외부 열에 대한 입력 열 매핑으로 입력 열이 매개 변수에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-110">The parameter values are stored in external columns in the transformation input, and mapping an input column to an external column maps an input column to a parameter.</span></span> <span data-ttu-id="b97f2-111">예를 들어 **ProductKey** 열의 값에 따라 **DimProduct** 테이블에서 행을 찾고 삭제하려면 **Param_0** 이라는 외부 열을 **ProductKey** 라는 입력 열에 매핑한 후 `DELETE FROM DimProduct WHERE ProductKey = ?`SQL 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-111">For example, to locate rows in the **DimProduct** table by the value in their **ProductKey** column and then delete them, you can map the external column named **Param_0** to the input column named **ProductKey,** and then run the SQL statement `DELETE FROM DimProduct WHERE ProductKey = ?`..</span></span> <span data-ttu-id="b97f2-112">OLE DB 명령 변환에는 매개 변수 이름이 제공되며 이 이름은 수정될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-112">The OLE DB Command transformation provides the parameter names and you cannot modify them.</span></span> <span data-ttu-id="b97f2-113">매개 변수 이름은 **Param_0**, **Param_1**등입니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-113">The parameter names are **Param_0**, **Param_1**, and so on.</span></span>  
  
 <span data-ttu-id="b97f2-114">**고급 편집기** 대화 상자를 사용하여 OLE DB 명령 변환을 구성하는 경우 SQL 문의 매개 변수는 변환 입력의 외부 열에 자동으로 매핑될 수 있으며, 각 매개 변수의 특성은 **새로 고침** 단추를 클릭하여 정의될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-114">If you configure the OLE DB Command transformation by using the **Advanced Editor** dialog box, the parameters in the SQL statement may be mapped automatically to external columns in the transformation input, and the characteristics of each parameter defined, by clicking the **Refresh** button.</span></span> <span data-ttu-id="b97f2-115">하지만 OLE DB 명령 변환에서 사용되는 OLE DB Provider가 매개 변수로부터의 매개 변수 정보 파생을 지원하지 않으면 외부 열을 수동으로 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-115">However, if the OLE DB provider that the OLE DB Command transformation uses does not support deriving parameter information from the parameter, you must configure the external columns manually.</span></span> <span data-ttu-id="b97f2-116">즉, 외부 입력의 각 매개 변수에 대한 열을 변환에 추가하고, **Param_0**과 같은 이름을 사용하도록 열 이름을 업데이트하고, DBParamInfoFlags 속성의 값을 지정하고, 매개 변수 값이 포함된 입력 열을 외부 열로 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-116">This means that you must add a column for each parameter to the external input to the transformation, update the column names to use names like **Param_0**, specify the value of the DBParamInfoFlags property, and map the input columns that contain parameter values to the external columns.</span></span>  
  
 <span data-ttu-id="b97f2-117">DBParamInfoFlags의 값은 매개 변수의 특성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-117">The value of DBParamInfoFlags represents the characteristics of the parameter.</span></span> <span data-ttu-id="b97f2-118">예를 들어 값 **1** 은 매개 변수가 입력 매개 변수임을 지정하며, 값 **65** 는 매개 변수가 입력 매개 변수이고 Null 값이 포함될 수 있음을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-118">For example, the value **1** specifies that the parameter is an input parameter, and the value **65** specifies that the parameter is an input parameter and may contain a null value.</span></span> <span data-ttu-id="b97f2-119">값은 OLE DB DBPARAMFLAGSENUM 열거의 값과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-119">The values must match the values in the OLE DB DBPARAMFLAGSENUM enumeration.</span></span> <span data-ttu-id="b97f2-120">자세한 내용은 OLE DB 참조 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b97f2-120">For more information, see the OLE DB reference documentation.</span></span>  
  
 <span data-ttu-id="b97f2-121">OLE DB 명령 변환은 `SQLCommand` 사용자 지정 속성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-121">The OLE DB Command transformation includes the `SQLCommand` custom property.</span></span> <span data-ttu-id="b97f2-122">이 속성은 패키지가 로드되면 속성 식을 사용하여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-122">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="b97f2-123">자세한 내용은 [Integration Services&#40;SSIS&#41; 식](../../expressions/integration-services-ssis-expressions.md), [패키지에서 속성 식 사용](../../expressions/use-property-expressions-in-packages.md) 및 [변환 사용자 지정 속성](transformation-custom-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b97f2-123">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="b97f2-124">이 변환에는 하나의 입력, 하나의 일반 출력 및 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-124">This transformation has one input, one regular output, and one error output.</span></span>  
  
## <a name="logging"></a><span data-ttu-id="b97f2-125">로깅</span><span class="sxs-lookup"><span data-stu-id="b97f2-125">Logging</span></span>  
 <span data-ttu-id="b97f2-126">OLE DB 명령 변환이 외부 데이터 공급자에 대해 수행하는 호출을 로깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-126">You can log the calls that the OLE DB Command transformation makes to external data providers.</span></span> <span data-ttu-id="b97f2-127">이 로깅 기능을 사용하여 OLE DB 명령 변환이 수행하는 외부 데이터 원본에 대한 연결 및 명령 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-127">You can use this logging capability to troubleshoot the connections and commands to external data sources that the OLE DB Command transformation performs.</span></span> <span data-ttu-id="b97f2-128">OLE DB 명령 변환이 외부 데이터 공급자에 대해 수행하는 호출을 로깅하려면 패키지 로깅을 설정하고 패키지 수준에서 **Diagnostic** 이벤트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-128">To log the calls that the OLE DB Command transformation makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="b97f2-129">자세한 내용은 [패키지 실행 문제 해결 도구](../../troubleshooting/troubleshooting-tools-for-package-execution.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b97f2-129">For more information, see [Troubleshooting Tools for Package Execution](../../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b97f2-130">관련 작업</span><span class="sxs-lookup"><span data-stu-id="b97f2-130">Related Tasks</span></span>  
 <span data-ttu-id="b97f2-131">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너 또는 개체 모델을 사용하여 변환을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b97f2-131">You can configure the transformation by either using the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or the object model.</span></span> <span data-ttu-id="b97f2-132">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하여 변환을 구성하는 방법은  [OLE DB 명령 변환 구성](../../configure-the-ole-db-command-transformation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b97f2-132">For details about configuring the transformation using the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] designer, see  [Configure the OLE DB Command Transformation](../../configure-the-ole-db-command-transformation.md).</span></span> <span data-ttu-id="b97f2-133">프로그래밍 방식으로 이 변환을 구성하는 방법은 개발자 가이드를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b97f2-133">See the Developer Guide for details about programmatically configuring this transformation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b97f2-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b97f2-134">See Also</span></span>  
 <span data-ttu-id="b97f2-135">[데이터 흐름](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="b97f2-135">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="b97f2-136">Integration Services 변환</span><span class="sxs-lookup"><span data-stu-id="b97f2-136">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
