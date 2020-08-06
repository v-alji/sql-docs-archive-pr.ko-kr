---
title: 다중 서버 환경에 적합 한 SQL Server 에이전트 서비스 계정 선택 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- multiserver environments [SQL Server], SQL Server Agent service account behavior
ms.assetid: a07e2f38-281c-495b-965b-13fad03ba548
author: stevestein
ms.author: sstein
ms.openlocfilehash: 94ef890f5d2ef2b85d2f4d1023a93747e903a7f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660848"
---
# <a name="choose-the-right-sql-server-agent-service-account-for-multiserver-environments"></a><span data-ttu-id="e21bf-102">다중 서버 환경에 적합한 SQL Server 에이전트 서비스 계정 선택</span><span class="sxs-lookup"><span data-stu-id="e21bf-102">Choose the Right SQL Server Agent Service Account for Multiserver Environments</span></span>
  <span data-ttu-id="e21bf-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스에 대해 선택한 Windows 계정은 다음과 같이 다중 서버 환경의 동작에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e21bf-103">The Windows account you choose for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service can affect the behavior of a multiserver environment, as follows:</span></span>  
  
-   <span data-ttu-id="e21bf-104">로컬 Windows Administrators 그룹의 멤버가 아닌 계정으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스를 실행하는 경우 대상 서버를 마스터 서버에 참여시키면 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e21bf-104">If you run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service under an account that is not a member of the local Windows Administrators group, enlisting target servers to master servers may fail.</span></span> <span data-ttu-id="e21bf-105">실패 시 다음 오류 메시지가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e21bf-105">If it does, the following error message is returned:</span></span>  
  
     <span data-ttu-id="e21bf-106">"참여 작업이 실패했습니다."</span><span class="sxs-lookup"><span data-stu-id="e21bf-106">"The enlistment operation failed."</span></span>  
  
     <span data-ttu-id="e21bf-107">이 문제를 해결하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스를 다시 시작하십시오.</span><span class="sxs-lookup"><span data-stu-id="e21bf-107">Restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent services to resolve this issue.</span></span>  
  
-   <span data-ttu-id="e21bf-108">로컬 시스템 계정으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스를 실행하는 경우 마스터 서버와 대상 서버가 같은 컴퓨터에 있는 경우에만 마스터 서버-대상 서버 작업이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e21bf-108">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is run under the Local System account, master server-target server operations are supported only if both the master server and the target server reside on the same computer.</span></span> <span data-ttu-id="e21bf-109">이 구성을 사용하면 대상 서버를 마스터 서버에 참여시킬 때 다음 메시지가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e21bf-109">If you use this configuration, the following message is returned when you enlist target servers to a master server:</span></span>  
  
     <span data-ttu-id="e21bf-110">"*<target_server_computer_name>* 의 에이전트 시작 계정에 대상 서버로 로그인할 권한이 있는지 확인하세요."</span><span class="sxs-lookup"><span data-stu-id="e21bf-110">"Ensure the agent start-up account for *<target_server_computer_name>* has rights to log on as targetServer."</span></span>  
  
     <span data-ttu-id="e21bf-111">이 정보 메시지는 무시해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e21bf-111">You can ignore this informational message.</span></span> <span data-ttu-id="e21bf-112">참여 작업이 성공적으로 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="e21bf-112">The enlistment operation should complete successfully.</span></span>  
  
 <span data-ttu-id="e21bf-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스에 대한 계정을 선택하는 방법에 대한 자세한 내용은 [SQL Server 에이전트 서비스의 계정 선택](select-an-account-for-the-sql-server-agent-service.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e21bf-113">For more information about choosing an account for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md).</span></span>  
  
  
