---
title: Excel 연결 관리자 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelconnection.f1
helpviewer_keywords:
- Excel Connection Manager Editor
ms.assetid: 7ff097e4-cafb-4885-a898-05b2a46628c1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f66de13b710e5ccb577e6f2d67c215572e34767
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651798"
---
# <a name="excel-connection-manager-editor"></a><span data-ttu-id="e1cdd-102">Excel 연결 관리자 편집기</span><span class="sxs-lookup"><span data-stu-id="e1cdd-102">Excel Connection Manager Editor</span></span>
  <span data-ttu-id="e1cdd-103">**Excel 연결 관리자 편집기** 대화 상자를 사용하여 기존 또는 새 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 통합 문서 파일에 대한 연결을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdd-103">Use the **Excel Connection Manager Editor** dialog box to add a connection to an existing or a new [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] workbook file.</span></span>  
  
 <span data-ttu-id="e1cdd-104">Excel 연결 관리자에 대한 자세한 내용은 [Excel Connection Manager](connection-manager/excel-connection-manager.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e1cdd-104">To learn more about the Excel connection manager, see [Excel Connection Manager](connection-manager/excel-connection-manager.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e1cdd-105">암호로 보호된 Excel 파일에는 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdd-105">You cannot connect to a password-protected Excel file.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e1cdd-106">옵션</span><span class="sxs-lookup"><span data-stu-id="e1cdd-106">Options</span></span>  
 <span data-ttu-id="e1cdd-107">**Excel 파일 경로**</span><span class="sxs-lookup"><span data-stu-id="e1cdd-107">**Excel file path**</span></span>  
 <span data-ttu-id="e1cdd-108">기존 또는 새 Excel 통합 문서 파일(.xls)의 경로와 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdd-108">Type the path and file name of an existing or a new Excel workbook file (.xls).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="e1cdd-109">새/존재 하지 않는 파일을 가리키는 **Excel 연결** 을 선택한 다음 **Excel 시트의 이름**에서 **새로 만들기** 를 클릭 하면 Excel **대상 편집기** 에서 자동으로 excel 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdd-109">The **Excel Destination Editor** automatically creates the Excel file when you select an **Excel Connection** that points to a new/non-existent file and then click **New** for **Name of the Excel Sheet**.</span></span>  
  
 <span data-ttu-id="e1cdd-110">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="e1cdd-110">**Browse**</span></span>  
 <span data-ttu-id="e1cdd-111">**열기** 대화 상자를 사용하여 Excel 파일이 있는 폴더 또는 새 파일을 만들려는 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdd-111">Use the **Open** dialog box to navigate to the folder in which the excel file exists or where you want to create the new file.</span></span>  
  
 <span data-ttu-id="e1cdd-112">**Excel 버전**</span><span class="sxs-lookup"><span data-stu-id="e1cdd-112">**Excel version**</span></span>  
 <span data-ttu-id="e1cdd-113">파일을 만드는 데 사용된 Microsoft Excel 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdd-113">Specify the version of Microsoft Excel that was used to create the file.</span></span>  
  
|<span data-ttu-id="e1cdd-114">옵션</span><span class="sxs-lookup"><span data-stu-id="e1cdd-114">Option</span></span>|<span data-ttu-id="e1cdd-115">Description</span><span class="sxs-lookup"><span data-stu-id="e1cdd-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e1cdd-116">Excel 97-2003</span><span class="sxs-lookup"><span data-stu-id="e1cdd-116">Excel 97-2003</span></span>|<span data-ttu-id="e1cdd-117">Excel 97 이상을 사용하여 파일을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdd-117">File was created using Excel 97 or later.</span></span>|  
|<span data-ttu-id="e1cdd-118">Excel 3.0</span><span class="sxs-lookup"><span data-stu-id="e1cdd-118">Excel 3.0</span></span>|<span data-ttu-id="e1cdd-119">파일이 Excel 3.0를 사용 하 여 만들어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdd-119">File was created using Excel 3.0.</span></span>|  
|<span data-ttu-id="e1cdd-120">Excel 4.0</span><span class="sxs-lookup"><span data-stu-id="e1cdd-120">Excel 4.0</span></span>|<span data-ttu-id="e1cdd-121">Excel 4.0을 사용하여 파일을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdd-121">File was created using Excel 4.0.</span></span>|  
|<span data-ttu-id="e1cdd-122">Excel 5.0</span><span class="sxs-lookup"><span data-stu-id="e1cdd-122">Excel 5.0</span></span>|<span data-ttu-id="e1cdd-123">Excel 95(7.0)를 사용하여 파일을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdd-123">File was created using Excel 95 (7.0).</span></span>|  
  
 <span data-ttu-id="e1cdd-124">**첫 번째 행에 열 이름 있음**</span><span class="sxs-lookup"><span data-stu-id="e1cdd-124">**First row has column names**</span></span>  
 <span data-ttu-id="e1cdd-125">선택한 워크시트의 첫 데이터 행에 열 이름이 포함되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdd-125">Specify whether the first row of data in the selected worksheet contains column names.</span></span> <span data-ttu-id="e1cdd-126">이 옵션의 기본값은 **True**입니다.</span><span class="sxs-lookup"><span data-stu-id="e1cdd-126">The default value of this option is **True**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1cdd-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e1cdd-127">See Also</span></span>  
 <span data-ttu-id="e1cdd-128">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e1cdd-128">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="e1cdd-129">Foreach 루프 컨테이너를 사용하여 Excel 파일 및 테이블 루핑</span><span class="sxs-lookup"><span data-stu-id="e1cdd-129">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
