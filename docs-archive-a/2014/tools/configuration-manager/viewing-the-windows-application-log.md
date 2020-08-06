---
title: Windows 애플리케이션 로그 보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- application logs [SQL Server]
- Windows application logs [SQL Server]
- viewing Windows application logs
- errors [SQL Server], logs
- system logs [SQL Server]
- security logs [SQL Server]
- displaying Windows application logs
- logs [SQL Server], Windows application logs
ms.assetid: f9853b74-7db7-47cc-b957-e49ed5bc0a1a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 22f900a0b203e652bbc9cc6e9638711d138756c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650325"
---
# <a name="viewing-the-windows-application-log"></a><span data-ttu-id="b16e6-102">Windows 애플리케이션 로그 보기</span><span class="sxs-lookup"><span data-stu-id="b16e6-102">Viewing the Windows Application Log</span></span>
  <span data-ttu-id="b16e6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 Microsoft Windows 애플리케이션 로그를 사용하도록 구성된 경우 각 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 세션은 이 로그에 새 이벤트를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="b16e6-103">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured to use the Microsoft Windows application log, each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] session writes new events to that log.</span></span> <span data-ttu-id="b16e6-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그와는 달리 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 시작할 때마다 새 애플리케이션 로그가 생성되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b16e6-104">Unlike the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, a new application log is not created each time you start an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b16e6-105">Windows 이벤트 뷰어 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 로그 뷰어를 사용하여 Windows 애플리케이션 로그를 보고 관리하십시오.</span><span class="sxs-lookup"><span data-stu-id="b16e6-105">View and manage the Windows application log by using Windows Event Viewer or the Log Viewer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="b16e6-106">이벤트 뷰어로 볼 수 있는 로그에는 세 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b16e6-106">There are three logs that can be viewed with Event Viewer.</span></span>  
  
|<span data-ttu-id="b16e6-107">Windows 로그 유형</span><span class="sxs-lookup"><span data-stu-id="b16e6-107">Windows log type</span></span>|<span data-ttu-id="b16e6-108">Description</span><span class="sxs-lookup"><span data-stu-id="b16e6-108">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="b16e6-109">시스템 로그</span><span class="sxs-lookup"><span data-stu-id="b16e6-109">System log</span></span>|<span data-ttu-id="b16e6-110">Windows 운영 체제 구성 요소에서 로그한 이벤트를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="b16e6-110">Records events logged by the Windows operating system components.</span></span> <span data-ttu-id="b16e6-111">예를 들어 시작할 때 드라이버나 다른 시스템 구성 요소 로드를 실패했으면 시스템 로그에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="b16e6-111">For example, the failure of a driver or other system component to load during startup is recorded in the system log.</span></span>|  
|<span data-ttu-id="b16e6-112">보안 로그</span><span class="sxs-lookup"><span data-stu-id="b16e6-112">Security log</span></span>|<span data-ttu-id="b16e6-113">실패한 로그인 시도와 같은 보안 이벤트를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="b16e6-113">Records security events, such as failed login attempts.</span></span> <span data-ttu-id="b16e6-114">이것은 보안 시스템의 변경 내용을 추적하고 일어날 수도 있는 보안 침해를 식별할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="b16e6-114">This helps track changes to the security system and identify possible breaches to security.</span></span> <span data-ttu-id="b16e6-115">예를 들어 시스템 로그온 시도는 사용자 관리자의 감사 설정에 따라 보안 로그에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="b16e6-115">For example, attempts to log on to the system may be recorded in the security log, depending on the audit settings in the User Manager.</span></span><br /><br /> <span data-ttu-id="b16e6-116">보안 로그를 보려면 **sysadmin** 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b16e6-116">Only members of the **sysadmin** fixed server role can view the security log.</span></span>|  
|<span data-ttu-id="b16e6-117">애플리케이션 로그</span><span class="sxs-lookup"><span data-stu-id="b16e6-117">Application log</span></span>|<span data-ttu-id="b16e6-118">애플리케이션에서 로그한 이벤트를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="b16e6-118">Records events that are logged by applications.</span></span> <span data-ttu-id="b16e6-119">예를 들어 데이터베이스 애플리케이션은 파일 오류를 애플리케이션 로그에 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b16e6-119">For example, a database application might record a file error in the application log.</span></span>|  
  
 <span data-ttu-id="b16e6-120">이벤트 뷰어 사용, 애플리케이션 로그 관리 및 표시된 정보를 이해하는 방법은 Windows 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b16e6-120">For more information about using Event Viewer, managing the application log, and understanding the information it presents, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="b16e6-121">**Windows 애플리케이션 로그를 보려면**</span><span class="sxs-lookup"><span data-stu-id="b16e6-121">**To view the Windows application log**</span></span>  
  
 [<span data-ttu-id="b16e6-122">Windows 애플리케이션 로그 보기&#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="b16e6-122">View the Windows Application Log &#40;Windows&#41;</span></span>](../../relational-databases/performance/view-the-windows-application-log-windows-10.md)  
  
  
