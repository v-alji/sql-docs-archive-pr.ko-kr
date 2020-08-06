---
title: 프로그래밍 방식으로 패키지 저장 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- programmatically saving a package
- saving a package programmatically
ms.assetid: 4204f817-d5df-475a-9338-d7f01305d566
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2879c4213b2c9c0bf395c103de0d1bc37e4daab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649138"
---
# <a name="saving-a-package-programmatically"></a><span data-ttu-id="90a51-102">프로그래밍 방식으로 패키지 저장</span><span class="sxs-lookup"><span data-stu-id="90a51-102">Saving a Package Programmatically</span></span>
  <span data-ttu-id="90a51-103">프로그래밍 방식으로 새 패키지를 작성하거나 기존 패키지를 수정한 후에는 일반적으로 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="90a51-103">After building a new package programmatically, or modifying an existing one, you usually want to save your changes.</span></span>  
  
 <span data-ttu-id="90a51-104">이 항목에서 설명하는 패키지 저장 방법을 사용할 경우에는 항상 `Microsoft.SqlServer.ManagedDTS` 어셈블리에 대한 참조가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="90a51-104">All of the methods used in this topic to save packages require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="90a51-105">새 프로젝트에 참조를 추가한 후 `using` 또는 `Imports` 문을 사용하여 <xref:Microsoft.SqlServer.Dts.Runtime> 네임스페이스를 가져오십시오.</span><span class="sxs-lookup"><span data-stu-id="90a51-105">After you add the reference in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace with a `using` or `Imports` statement.</span></span>  
  
## <a name="saving-a-package-programmatically"></a><span data-ttu-id="90a51-106">프로그래밍 방식으로 패키지 저장</span><span class="sxs-lookup"><span data-stu-id="90a51-106">Saving a Package Programmatically</span></span>  
 <span data-ttu-id="90a51-107">프로그래밍 방식으로 패키지를 저장하려면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <xref:Microsoft.SqlServer.Dts.Runtime.Application> 클래스의 다음 메서드 중 하나를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="90a51-107">To save a package programmatically, call one of the following methods of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <xref:Microsoft.SqlServer.Dts.Runtime.Application> class:</span></span>  
  
|<span data-ttu-id="90a51-108">스토리지 위치</span><span class="sxs-lookup"><span data-stu-id="90a51-108">Storage Location</span></span>|<span data-ttu-id="90a51-109">호출할 메서드</span><span class="sxs-lookup"><span data-stu-id="90a51-109">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="90a51-110">파일</span><span class="sxs-lookup"><span data-stu-id="90a51-110">File</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToXml%2A>|  
|<span data-ttu-id="90a51-111">SSIS 패키지 저장소</span><span class="sxs-lookup"><span data-stu-id="90a51-111">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServer%2A><br /><br /> <span data-ttu-id="90a51-112">또는</span><span class="sxs-lookup"><span data-stu-id="90a51-112">or</span></span><br /><br /> <xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServerAs%2A>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="90a51-113">SSIS 패키지 저장소를 사용하기 위한 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 클래스의 메서드는 "." 또는 로컬 서버의 서버 이름만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="90a51-113">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store only support "." or the server name for the local server.</span></span> <span data-ttu-id="90a51-114">"(local)" 또는 "localhost"는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="90a51-114">You cannot use "(local)" or "localhost".</span></span>  
  
<span data-ttu-id="90a51-115">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="90a51-115">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="90a51-116">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="90a51-116">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="90a51-117">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="90a51-117">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="90a51-118">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="90a51-118">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90a51-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="90a51-119">See Also</span></span>  
 [<span data-ttu-id="90a51-120">패키지 저장</span><span class="sxs-lookup"><span data-stu-id="90a51-120">Save Packages</span></span>](../save-packages.md)  
  
  
