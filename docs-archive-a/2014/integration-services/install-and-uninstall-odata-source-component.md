---
title: OData 원본 구성 요소 설치 및 제거 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0a3ae788-e8c8-4a4d-bb15-34c673abcd17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fad0a86c6226f408b0495569d0a853dd7340aeca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651187"
---
# <a name="install-and-uninstall-odata-source-component"></a><span data-ttu-id="ec663-102">OData 원본 구성 요소 설치 및 제거</span><span class="sxs-lookup"><span data-stu-id="ec663-102">Install and Uninstall OData Source Component</span></span>
  <span data-ttu-id="ec663-103">이 항목에서는 컴퓨터에서 OData 원본 구성 요소를 설치하거나 제거하기 위한 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ec663-103">This topic provides instructions for installing or removing OData Source Component on your computer.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="ec663-104">설치</span><span class="sxs-lookup"><span data-stu-id="ec663-104">Installation</span></span>  
 <span data-ttu-id="ec663-105">OData 원본 구성 요소를 사용하려면 다음과 같은 필수 구성 요소가 컴퓨터에 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec663-105">The OData Source Component requires following prerequisite components to be installed on your computer.</span></span>  
  
-   <span data-ttu-id="ec663-106">SQL Server Data Tools(패키지를 디자인하는 데 사용)</span><span class="sxs-lookup"><span data-stu-id="ec663-106">SQL Server Data Tools (to design packages)</span></span>  
  
-   <span data-ttu-id="ec663-107">SQL Server Integration Services(Visual Studio 외부에서 패키지를 실행하는 데 사용)</span><span class="sxs-lookup"><span data-stu-id="ec663-107">SQL Server Integration Services (to run packages outside Visual Studio)</span></span>  
  
 <span data-ttu-id="ec663-108">OData 원본 구성 요소를 설치하려면 [SQL Server 2014 기능 팩](https://go.microsoft.com/fwlink/p/?LinkId=391999) 을 다운로드하고 다음 MSI 파일 중 하나를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ec663-108">To install the OData Source Component, download [SQL Server 2014 Feature Pack](https://go.microsoft.com/fwlink/p/?LinkId=391999) and run one of the following MSI files.</span></span>  
  
-   <span data-ttu-id="ec663-109">ODataSourceForSQLServer2014-amd64.msi(64비트 플랫폼의 경우)</span><span class="sxs-lookup"><span data-stu-id="ec663-109">ODataSourceForSQLServer2014-amd64.msi for 64bit platforms</span></span>  
  
-   <span data-ttu-id="ec663-110">ODataSourceForSQLServer2014-x86.msi(32비트 플랫폼의 경우)</span><span class="sxs-lookup"><span data-stu-id="ec663-110">ODataSourceForSQLServer2014-x86.msi for 32bit platforms</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ec663-111">64비트 설치 관리자는 32비트 및 64비트 버전의 OData 원본 구성 요소를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ec663-111">The 64bit installer will install both 32bit and 64bit versions of the OData Source Component.</span></span> <span data-ttu-id="ec663-112">32비트 OS를 사용하는 경우에는 32비트 설치 관리자를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec663-112">You only need to run the 32bit installer if you are using a 32bit OS.</span></span>  
  
## <a name="uninstallation"></a><span data-ttu-id="ec663-113">제거</span><span class="sxs-lookup"><span data-stu-id="ec663-113">Uninstallation</span></span>  
 <span data-ttu-id="ec663-114">OData 원본 구성 요소는 **프로그램 및 기능** 메뉴에서 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec663-114">The OData Source component can be uninstalled from the **Programs and Features** menu.</span></span> <span data-ttu-id="ec663-115">**Microsoft SQL Server SSIS OData 원본 구성 요소(x64)** 항목을 찾고 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ec663-115">Find the **Microsoft SQL Server SSIS OData Source Component (x64)** entry and click **Uninstall**.</span></span>  
  
  
