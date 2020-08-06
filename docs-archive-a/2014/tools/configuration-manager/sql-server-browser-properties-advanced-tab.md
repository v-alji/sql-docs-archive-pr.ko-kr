---
title: SQL Server Browser 속성(고급 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ba79137a-cb72-4bf3-a650-e11d02cfce10
author: stevestein
ms.author: sstein
ms.openlocfilehash: 480cd93c3feca44dd455a1a9ce2fd12994ca6100
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659756"
---
# <a name="sql-server-browser-properties-advanced-tab"></a><span data-ttu-id="1e3d6-102">SQL Server Browser 속성(고급 탭)</span><span class="sxs-lookup"><span data-stu-id="1e3d6-102">SQL Server Browser Properties (Advanced Tab)</span></span>
  <span data-ttu-id="1e3d6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 프로그램은 서버에서 서비스로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e3d6-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser program runs as a service on the server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1e3d6-104">Browser는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 리소스에 대해 들어오는 요청을 수신 대기하고 컴퓨터에 설치된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3d6-104">Browser listens for incoming requests for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources and provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1e3d6-105">옵션</span><span class="sxs-lookup"><span data-stu-id="1e3d6-105">Options</span></span>  
 <span data-ttu-id="1e3d6-106">**클러스터형**</span><span class="sxs-lookup"><span data-stu-id="1e3d6-106">**Clustered**</span></span>  
 <span data-ttu-id="1e3d6-107">이 서비스가 클러스터형 서버의 리소스로 설치되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e3d6-107">Indicates if this service is installed as a resource of a clustered server.</span></span>  
  
 <span data-ttu-id="1e3d6-108">**고객 의견 보내기**</span><span class="sxs-lookup"><span data-stu-id="1e3d6-108">**Customer Feedback Reporting**</span></span>  
 <span data-ttu-id="1e3d6-109">이 서비스에 대해 서비스 품질 모니터링이 활성화되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e3d6-109">Indicates whether Service Quality Monitoring has been enabled on this service.</span></span> <span data-ttu-id="1e3d6-110">고객 의견 보고에 대한 자세한 내용은 온라인 설명서에서 "오류 및 사용 보고서 설정" 항목을 참고하십시오.</span><span class="sxs-lookup"><span data-stu-id="1e3d6-110">For more information on Customer Feedback Reporting, search Books Online for the topic, "Error and Usage Report Settings."</span></span>  
  
 <span data-ttu-id="1e3d6-111">**덤프 디렉터리**</span><span class="sxs-lookup"><span data-stu-id="1e3d6-111">**Dump Directory**</span></span>  
 <span data-ttu-id="1e3d6-112">오류 발생 시 메모리 덤프가 추가될 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="1e3d6-112">The location where memory dumps are placed in case of an error.</span></span>  
  
 <span data-ttu-id="1e3d6-113">**오류 보고**</span><span class="sxs-lookup"><span data-stu-id="1e3d6-113">**Error Reporting**</span></span>  
 <span data-ttu-id="1e3d6-114">이 속성을 **예**로 설정하면 오류 발생 시 Dr. Watson 프로그램에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 또는 사용자의 오류 서버로 정보를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="1e3d6-114">When set to **Yes**, the Dr. Watson program forwards information to either [!INCLUDE[msCoName](../../includes/msconame-md.md)] or your error server if a serious failure occurs.</span></span> <span data-ttu-id="1e3d6-115">오류 보고에 대한 자세한 내용은 온라인 설명서에서 "오류 및 사용 보고서 설정" 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1e3d6-115">For more information on Error Reporting, search Books Online for the topic, "Error and Usage Report Settings."</span></span>  
  
 <span data-ttu-id="1e3d6-116">**인스턴스 ID**</span><span class="sxs-lookup"><span data-stu-id="1e3d6-116">**Instance ID**</span></span>  
 <span data-ttu-id="1e3d6-117">이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 인스턴스를 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e3d6-117">Indicates the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that used this [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent instance.</span></span> <span data-ttu-id="1e3d6-118">기본 인스턴스는 **MSSQL10_50.MSSQLSERVER**입니다.</span><span class="sxs-lookup"><span data-stu-id="1e3d6-118">The default instance is **MSSQL10_50.MSSQLSERVER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e3d6-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e3d6-119">See Also</span></span>  
 [<span data-ttu-id="1e3d6-120">SQL Server Browser 서비스</span><span class="sxs-lookup"><span data-stu-id="1e3d6-120">SQL Server Browser Service</span></span>](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
