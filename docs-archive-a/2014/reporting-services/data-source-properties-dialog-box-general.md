---
title: 데이터 원본 속성 대화 상자, 일반 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasourceproperties.general.f1
- "10120"
ms.assetid: 44b5edd3-5c11-4d3d-91b8-5871aa0572ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c79ad70cdd4dcb10e1abce1102fa39eef4c67461
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639411"
---
# <a name="data-source-properties-dialog-box-general"></a><span data-ttu-id="fa3de-102">데이터 원본 속성 대화 상자, 일반</span><span class="sxs-lookup"><span data-stu-id="fa3de-102">Data Source Properties Dialog Box, General</span></span>
  <span data-ttu-id="fa3de-103">**데이터 원본 속성** 대화 상자의 **일반** 을 선택하여 보고서의 데이터 원본에 대한 연결 정보를 표시하고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa3de-103">Select **General** on the **Data Source Properties** dialog box to display and modify connection information for a data source in the report.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fa3de-104">옵션</span><span class="sxs-lookup"><span data-stu-id="fa3de-104">Options</span></span>  
 <span data-ttu-id="fa3de-105">**이름**</span><span class="sxs-lookup"><span data-stu-id="fa3de-105">**Name**</span></span>  
 <span data-ttu-id="fa3de-106">데이터 원본의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fa3de-106">Type the name of the data source.</span></span> <span data-ttu-id="fa3de-107">데이터 원본 이름은 보고서 내에서 중복되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa3de-107">The data source name must be unique within the report.</span></span> <span data-ttu-id="fa3de-108">기본적으로 DataSource1 또는 DataSource2 같은 일반 이름이 데이터 원본에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa3de-108">By default, a general name, such as DataSource1 or DataSource2, is assigned to the data source.</span></span>  
  
 <span data-ttu-id="fa3de-109">**포함된 연결**</span><span class="sxs-lookup"><span data-stu-id="fa3de-109">**Embedded connection**</span></span>  
 <span data-ttu-id="fa3de-110">공유 데이터 원본을 사용하지 않으려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fa3de-110">Select this option when you do not want to use a shared data source.</span></span>  
  
 <span data-ttu-id="fa3de-111">**형식**</span><span class="sxs-lookup"><span data-stu-id="fa3de-111">**Type**</span></span>  
 <span data-ttu-id="fa3de-112">데이터 처리 확장 프로그램을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fa3de-112">Select a data processing extension.</span></span> <span data-ttu-id="fa3de-113">등록된 확장 프로그램이 목록에 모두 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa3de-113">The list displays all registered extensions.</span></span>  
  
 <span data-ttu-id="fa3de-114">**연결 문자열**</span><span class="sxs-lookup"><span data-stu-id="fa3de-114">**Connection string**</span></span>  
 <span data-ttu-id="fa3de-115">데이터 원본에 대한 연결 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fa3de-115">Enter a connection string for the data source.</span></span> <span data-ttu-id="fa3de-116">**연결 속성** 대화 상자를 사용하여 연결 문자열을 작성하려면 **편집** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fa3de-116">Click **Edit** to build the connection string using the **Connection Properties** dialog box.</span></span> <span data-ttu-id="fa3de-117">식을 편집하려면 **식** (*fx*) 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fa3de-117">Click the **Expressions** (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="fa3de-118">**공유 데이터 원본 참조 사용**</span><span class="sxs-lookup"><span data-stu-id="fa3de-118">**Use shared data source reference**</span></span>  
 <span data-ttu-id="fa3de-119">공유 데이터 원본에 연결하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fa3de-119">Select this option to link to a shared data source.</span></span> <span data-ttu-id="fa3de-120">드롭다운 목록에서 공유 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fa3de-120">Select a shared data source from the drop-down list.</span></span> <span data-ttu-id="fa3de-121">선택한 데이터 원본을 편집하려면 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fa3de-121">To edit the selected data source, click **Edit**.</span></span> <span data-ttu-id="fa3de-122">**공유 데이터 원본 참조 사용** 을 선택하면 **유형** 및 **연결 문자열** 이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa3de-122">If **Use shared data source reference** is selected, **Type** and **Connection string** are disabled.</span></span>  
  
 <span data-ttu-id="fa3de-123">**쿼리 처리 시 단일 트랜잭션 사용**</span><span class="sxs-lookup"><span data-stu-id="fa3de-123">**Use a single transaction when processing the queries**</span></span>  
 <span data-ttu-id="fa3de-124">이 데이터 원본을 사용하는 데이터 세트가 데이터베이스에 대해 단일 트랜잭션에서 실행되도록 지정하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fa3de-124">Select this option to indicate that datasets that use this data source are run in a single transaction against the database.</span></span> <span data-ttu-id="fa3de-125">동일한 데이터 원본을 사용하는 하위 보고서에 대한 트랜잭션을 포함하려면 **속성** 창에서 하위 보고서의 **기타** 속성과 관련하여 **MergeTransactions** 를 **True** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa3de-125">To include transactions for subreports that use the same data source, set **MergeTransactions** to **True** in the subreport's **Other** properties section of the **Properties** pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa3de-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fa3de-126">See Also</span></span>  
 <span data-ttu-id="fa3de-127">[보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fa3de-127">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="fa3de-128">[SSRS&#41;&#40;포함 된 데이터 원본 또는 공유 데이터 원본 만들기](../../2014/reporting-services/create-an-embedded-or-shared-data-source-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fa3de-128">[Create an Embedded or Shared Data Source &#40;SSRS&#41;](../../2014/reporting-services/create-an-embedded-or-shared-data-source-ssrs.md) </span></span>  
 <span data-ttu-id="fa3de-129">[Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="fa3de-129">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="fa3de-130">데이터 원본 속성 대화 상자, 자격 증명</span><span class="sxs-lookup"><span data-stu-id="fa3de-130">Data Source Properties Dialog Box, Credentials</span></span>](../../2014/reporting-services/data-source-properties-dialog-box-credentials.md)  
  
  
