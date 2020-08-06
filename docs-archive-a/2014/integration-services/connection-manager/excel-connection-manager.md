---
title: Excel 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- files [Integration Services], connections
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7561361c6d4ab7e22282b25367906aa4b75e5bc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650236"
---
# <a name="excel-connection-manager"></a><span data-ttu-id="7ac91-102">Excel 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="7ac91-102">Excel Connection Manager</span></span>
  <span data-ttu-id="7ac91-103">Excel 연결 관리자를 사용하면 패키지에서 기존 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 통합 문서 파일에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac91-103">An Excel connection manager enables a package to connect to an existing [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel workbook file.</span></span> <span data-ttu-id="7ac91-104">가 포함 된 excel 원본 및 excel 대상은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] excel 연결 관리자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac91-104">The Excel source and the Excel destination that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include use the Excel connection manager.</span></span>  
  
 <span data-ttu-id="7ac91-105">패키지에 Excel 연결 관리자를 추가하면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 런타임에 Excel 연결로 확인되는 연결 관리자를 만들고, 연결 관리자 속성을 설정하고, 연결 관리자를 패키지의 `Connections` 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac91-105">When you add an Excel connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that is resolved as an Excel connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="7ac91-106">연결 관리자의 `ConnectionManagerType` 속성이 `EXCEL`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ac91-106">The `ConnectionManagerType` property of the connection manager is set to `EXCEL`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7ac91-107">암호로 보호된 Excel 파일에는 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac91-107">You cannot connect to a password-protected Excel file.</span></span>  
  
## <a name="configuration-of-the-excel-connection-manager"></a><span data-ttu-id="7ac91-108">Excel 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="7ac91-108">Configuration of the Excel Connection Manager</span></span>  
 <span data-ttu-id="7ac91-109">다음과 같은 방법으로 Excel 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac91-109">You can configure the Excel connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="7ac91-110">Excel 통합 문서 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac91-110">Specify the path of the Excel workbook file.</span></span>  
  
-   <span data-ttu-id="7ac91-111">파일을 만드는 데 사용된 Excel 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7ac91-111">Specify the version of Excel that was used to create the file.</span></span>  
  
-   <span data-ttu-id="7ac91-112">선택한 워크시트 또는 범위에서 액세스한 첫 데이터 행에 열 이름이 포함되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7ac91-112">Indicate whether the first row of accessed data in the selected worksheets or ranges contains column names.</span></span>  
  
 <span data-ttu-id="7ac91-113">Excel 연결 관리자가 Excel 원본에 사용될 경우 열 이름이 추출한 데이터에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ac91-113">If the Excel connection manager is used by an Excel source, the column names are included with the extracted data.</span></span> <span data-ttu-id="7ac91-114">Excel 대상에 사용될 경우에는 열 이름이 기록된 데이터에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ac91-114">If it is used by an Excel destination, the column names are included in the written data.</span></span>  
  
 <span data-ttu-id="7ac91-115">Excel 연결 관리자는 Jet 4.0용 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB 공급자와 공급자에서 지원하는 Excel ISAM(Indexed Sequential Access Method) 드라이버를 사용하여 Excel 데이터 원본에 연결하고 데이터를 읽고 씁니다.</span><span class="sxs-lookup"><span data-stu-id="7ac91-115">The Excel connection manager uses the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 and its supporting Excel ISAM (Indexed Sequential Access Method) driver to connect and read and write data to Excel data sources.</span></span> <span data-ttu-id="7ac91-116">Excel 원본 및 Excel 대상에서 사용 하는 경우이 공급자와 드라이버의 동작에 대 한 자세한 내용은 [Excel 원본](../data-flow/excel-source.md) 및 [excel 대상](../data-flow/excel-destination.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7ac91-116">For more information about the behavior of this provider and driver when used with Excel sources and Excel destinations, see [Excel Source](../data-flow/excel-source.md) and [Excel Destination](../data-flow/excel-destination.md).</span></span>  
  
 <span data-ttu-id="7ac91-117">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ac91-117">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="7ac91-118">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용은 [Excel 연결 관리자 편집기](../excel-connection-manager-editor.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ac91-118">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Excel Connection Manager Editor](../excel-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="7ac91-119">연결 관리자를 프로그래밍 방식으로 구성하는 방법에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 및 [프로그래밍 방식으로 연결 추가](../building-packages-programmatically/adding-connections-programmatically.md)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ac91-119">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
 <span data-ttu-id="7ac91-120">Excel 파일 그룹을 통한 루핑 방법에 대한 자세한 내용은 [Foreach 루프 컨테이너를 사용하여 Excel 파일 및 테이블 루핑](../control-flow/foreach-loop-container.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ac91-120">For information about looping through a group of Excel files, see [Loop through Excel Files and Tables by Using a Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="7ac91-121">관련 작업</span><span class="sxs-lookup"><span data-stu-id="7ac91-121">Related Tasks</span></span>  
  
-   [<span data-ttu-id="7ac91-122">Foreach 루프 컨테이너를 사용하여 Excel 파일 및 테이블 루핑</span><span class="sxs-lookup"><span data-stu-id="7ac91-122">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](../control-flow/foreach-loop-container.md)  
  
-   [<span data-ttu-id="7ac91-123">SSIS(SQL Server Integration Services)를 사용하여 Excel에서 데이터 가져오기 또는 Excel로 데이터 내보내기</span><span class="sxs-lookup"><span data-stu-id="7ac91-123">Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)</span></span>](../load-data-to-from-excel-with-ssis.md)
  
  
