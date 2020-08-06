---
title: Excel Services에서 신뢰할 수 있는 Data Provider로 MSOLAP 추가 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c1f40fa4-de6d-41ee-8124-14b4d65988f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 876ec613f18b2d91b5e06ab5fed4a7b258c30a36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659683"
---
# <a name="add-msolap5-as-a-trusted-data-provider-in-excel-services"></a><span data-ttu-id="d5369-102">MSOLAP.5를 Excel 서비스에서 신뢰할 수 있는 데이터 공급자로 추가</span><span class="sxs-lookup"><span data-stu-id="d5369-102">Add MSOLAP.5 as a Trusted Data Provider in Excel Services</span></span>
  <span data-ttu-id="d5369-103">MSOLAP.5는 SQL Server 2012용 Analysis Services OLE DB 공급자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d5369-103">MSOLAP.5 refers to the Analysis Services OLE DB provider for SQL Server 2012.</span></span> <span data-ttu-id="d5369-104">Excel 서비스가 서버에서 PowerPivot 데이터를 사용할 수 있도록 하는 연결 요청을 만들려면 이 공급자를 신뢰해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5369-104">Excel Services must trust this provider before it will make the connection request that results in the availability of PowerPivot data on a server.</span></span>  
  
 <span data-ttu-id="d5369-105">PowerPivot 구성 도구를 사용하여 SharePoint용 PowerPivot을 구성한 경우 이 도구에는 이 요구 사항을 만족시키는 동작이 포함되어 있으므로 MSOLAP.5는 이미 신뢰할 수 있는 공급자일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5369-105">If you configured PowerPivot for SharePoint using the PowerPivot Configuration Tool, MSOLAP.5 might already be a trusted provider because the tool includes an action that satisfies this requirement.</span></span> <span data-ttu-id="d5369-106">그러나 PowerShell 또는 중앙 관리를 사용하거나 구성 도구에서 신뢰할 수 있는 공급자 동작을 제외한 경우에는 공급자가 누락될 수 있으며 이 경우에는 PowerPivot 데이터 액세스용 팜을 구성하는 작업의 일부로 지금 이 공급자를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5369-106">However, if you are using PowerShell, Central Administration, or if you excluded the trusted provider action in the configuration tool, the provider might be missing, which case you should add it now as part of configuring the farm for PowerPivot data access.</span></span>  
  
 <span data-ttu-id="d5369-107">각 Excel Services 서비스 애플리케이션에 대해 한 번씩 이 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5369-107">You only need to perform this step once for each Excel Services service application.</span></span>  
  
 <span data-ttu-id="d5369-108">SharePoint용 PowerPivot 서버나 Excel 서비스 서버처럼 PowerPivot 데이터 요청을 처리하는 각 물리적 서버는 해당 컴퓨터에 OLE DB 공급자가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5369-108">Each physical server that handles a PowerPivot data request, such as a PowerPivot for SharePoint server or an Excel Services server, must have the OLE DB provider installed on the computer.</span></span> <span data-ttu-id="d5369-109">SharePoint용 PowerPivot 설치에는 항상 OLE DB 공급자가 포함되지만 Excel 서비스가 실행되는 컴퓨터에 SharePoint용 PowerPivot이 없으면 공급자를 수동으로 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5369-109">A PowerPivot for SharePoint installation always includes the OLE DB provider, but if Excel Services is running on a computer that does not have PowerPivot for SharePoint, you must install the provider manually.</span></span> <span data-ttu-id="d5369-110">자세한 내용은 [SharePoint 서버에서 Analysis Services OLE DB 공급자 설치](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5369-110">For more information, see [Install the Analysis Services OLE DB Provider on SharePoint Servers](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).</span></span>  
  
## <a name="add-a-trusted-provider-to-excel-services"></a><span data-ttu-id="d5369-111">Excel 서비스에 신뢰할 수 있는 공급자 추가</span><span class="sxs-lookup"><span data-stu-id="d5369-111">Add a trusted provider to Excel Services</span></span>  
  
1.  <span data-ttu-id="d5369-112">중앙 관리에서 **서비스 애플리케이션 관리**를 클릭한 다음 Excel 서비스 애플리케이션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d5369-112">In Central Administration, click **Manage service applications**, and then click the Excel Services service application.</span></span>  
  
2.  <span data-ttu-id="d5369-113">**신뢰할 수 있는 데이터 공급자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d5369-113">Click **Trusted Data Providers**.</span></span>  
  
3.  <span data-ttu-id="d5369-114">MSOLAP.5가 목록에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d5369-114">Verify that MSOLAP.5 appears in the list.</span></span> <span data-ttu-id="d5369-115">SharePoint용 PowerPivot을 구성한 방법에 따라 MSOLAP.5가 이미 신뢰할 수 있는 공급자일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5369-115">Depending on how you configured PowerPivot for SharePoint, MSOLAP.5 might already be trusted.</span></span>  
  
4.  <span data-ttu-id="d5369-116">목록에 없으면 **신뢰할 수 있는 데이터 공급자 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d5369-116">If it is not listed, click **Add Trusted Data Provider**.</span></span>  
  
5.  <span data-ttu-id="d5369-117">공급자 ID에 `MSOLAP.5`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d5369-117">In Provider ID, type `MSOLAP.5`.</span></span>  
  
6.  <span data-ttu-id="d5369-118">공급자 유형에서 OLE DB가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d5369-118">For Provider Type, ensure that OLE DB is selected.</span></span>  
  
7.  <span data-ttu-id="d5369-119">공급자 설명에서 **Microsoft OLE DB Provider for OLAP Services 11.0**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d5369-119">In Provider Description, type **Microsoft OLE DB Provider for OLAP Services 11.0**.</span></span>  
  
  
