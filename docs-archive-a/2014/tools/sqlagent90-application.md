---
title: sqlagent90 응용 프로그램 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- starting SQL Server Agent
- sqlagent90 application
- SQL Server Agent, starting
- command prompt utilities [SQL Server], sqlagent90
ms.assetid: e8b80e8d-d0c9-4500-a868-0ce08233da08
author: stevestein
ms.author: sstein
ms.openlocfilehash: 290cb69f39aa3b08bb290c210b2d37977614a1ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648721"
---
# <a name="sqlagent90-application"></a><span data-ttu-id="9ee94-102">sqlagent90 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="9ee94-102">sqlagent90 Application</span></span>
  <span data-ttu-id="9ee94-103">**sqlagent90** 애플리케이션을 사용하면 명령 프롬프트에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ee94-103">The **sqlagent90** application starts [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent from the command prompt.</span></span> <span data-ttu-id="9ee94-104">일반적으로 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 를 통해 또는 애플리케이션에서 SQL-DMO 메서드를 사용하여 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 에이전트를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee94-104">Usually, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent should be run from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or by using SQL-SMO methods in an application.</span></span> <span data-ttu-id="9ee94-105">**에이전트를 진단하거나 주 지원 공급자가 지정하는 경우에만 명령 프롬프트에서** sqlagent90 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ee94-105">Only run **sqlagent90** from the command prompt when you are diagnosing [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent, or when you are directed to it by your primary support provider.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ee94-106">구문</span><span class="sxs-lookup"><span data-stu-id="9ee94-106">Syntax</span></span>  
  
```  
  
sqlagent90  
-c [-v] [-iinstance_name]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9ee94-107">인수</span><span class="sxs-lookup"><span data-stu-id="9ee94-107">Arguments</span></span>  
 <span data-ttu-id="9ee94-108">**-c**</span><span class="sxs-lookup"><span data-stu-id="9ee94-108">**-c**</span></span>  
 <span data-ttu-id="9ee94-109">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트가 명령 프롬프트에서 실행되고 Microsoft Windows 서비스 제어 관리자와 관계 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ee94-109">Indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent is running from the command prompt and is independent of the Microsoft Windows Services Control Manager.</span></span> <span data-ttu-id="9ee94-110">**-c** 를 사용하면 관리 도구의 서비스 애플리케이션 또는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 관리자에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트를 제어할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ee94-110">When **-c** is used, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent cannot be controlled from either the Services application in Administrative Tools or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="9ee94-111">이 인수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="9ee94-111">This argument is mandatory.</span></span>  
  
 <span data-ttu-id="9ee94-112">**-v**</span><span class="sxs-lookup"><span data-stu-id="9ee94-112">**-v**</span></span>  
 <span data-ttu-id="9ee94-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트를 자세한 정보 표시 모드로 실행하며 명령 프롬프트 창에 진단 정보를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee94-113">Indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent runs in verbose mode and writes diagnostic information to the command-prompt window.</span></span> <span data-ttu-id="9ee94-114">진단 정보는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 오류 로그에 기록되는 정보와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9ee94-114">The diagnostic information is the same as the information written to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent error log.</span></span>  
  
 <span data-ttu-id="9ee94-115">**-i** *instance_name*</span><span class="sxs-lookup"><span data-stu-id="9ee94-115">**-i** *instance_name*</span></span>  
 <span data-ttu-id="9ee94-116">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance_name [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 으로 지정한 명명된 *인스턴스에*에이전트가 연결됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ee94-116">Indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent connects to the named [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance specified by *instance_name*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ee94-117">설명</span><span class="sxs-lookup"><span data-stu-id="9ee94-117">Remarks</span></span>  
 <span data-ttu-id="9ee94-118">저작권 정보가 표시된 다음 **sqlagent90** 은 **-v** 스위치가 지정된 경우에만 명령 프롬프트 창에 출력을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9ee94-118">After displaying a copyright message, **sqlagent90** displays output in the command prompt window only when the **-v** switch is specified.</span></span> <span data-ttu-id="9ee94-119">**sqlagent90**을 중지하려면 명령 프롬프트에서 Ctrl+C를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9ee94-119">To stop **sqlagent90**, press CTRL+C at the command prompt.</span></span> <span data-ttu-id="9ee94-120">또한 **sqlagent90**을 중지하기 전에 먼저 명령 프롬프트 창을 닫지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="9ee94-120">Do not close the command-prompt window before stopping **sqlagent90**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ee94-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ee94-121">See Also</span></span>  
 [<span data-ttu-id="9ee94-122">관리 태스크 자동화&#40;SQL Server 에이전트&#41;</span><span class="sxs-lookup"><span data-stu-id="9ee94-122">Automated Administration Tasks &#40;SQL Server Agent&#41;</span></span>](../ssms/agent/automated-administration-tasks-sql-server-agent.md)  
  
  
