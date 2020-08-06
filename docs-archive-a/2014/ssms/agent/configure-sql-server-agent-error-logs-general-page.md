---
title: SQL Server 에이전트 오류 로그 구성(일반 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.errorlog.configure.f1
ms.assetid: e08de622-6f87-470c-aee0-b2d6cb6cca88
author: stevestein
ms.author: sstein
ms.openlocfilehash: bd4c083ea7e7d220d5da20594079b7679c0bb724
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652540"
---
# <a name="configure-sql-server-agent-error-logs-general-page"></a><span data-ttu-id="7a80a-102">SQL Server 에이전트 오류 로그 구성(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="7a80a-102">Configure SQL Server Agent Error Logs (General Page)</span></span>
  <span data-ttu-id="7a80a-103">이 화면을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 오류 로깅의 설정을 확인하고 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a80a-103">Use this screen to view and update settings for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error logging.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7a80a-104">옵션</span><span class="sxs-lookup"><span data-stu-id="7a80a-104">Options</span></span>  
 <span data-ttu-id="7a80a-105">**오류 로그 파일**</span><span class="sxs-lookup"><span data-stu-id="7a80a-105">**Error log file**</span></span>  
 <span data-ttu-id="7a80a-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 오류 로그를 쓸 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a80a-106">Specifies the file to which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent writes error logs.</span></span>  
  
 <span data-ttu-id="7a80a-107">**...**</span><span class="sxs-lookup"><span data-stu-id="7a80a-107">**...**</span></span>  
 <span data-ttu-id="7a80a-108">오류 로그 파일을 찾아봅니다.</span><span class="sxs-lookup"><span data-stu-id="7a80a-108">Browse to the error log file.</span></span>  
  
 <span data-ttu-id="7a80a-109">**OEM 오류 로그 쓰기**</span><span class="sxs-lookup"><span data-stu-id="7a80a-109">**Write OEM error log**</span></span>  
 <span data-ttu-id="7a80a-110">오류 로그 파일을 비유니코드 파일로 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="7a80a-110">Writes the error log file as a non-Unicode file.</span></span> <span data-ttu-id="7a80a-111">이렇게 하면 로그 파일에서 사용하는 디스크 공간의 양이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="7a80a-111">This reduces the amount of disk space consumed by the log file.</span></span> <span data-ttu-id="7a80a-112">그러나 이 옵션을 설정하면 유니코드 데이터가 포함된 메시지를 읽기가 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a80a-112">However, messages that include Unicode data may be more difficult to read when this option is enabled.</span></span>  
  
 <span data-ttu-id="7a80a-113">**Errors**</span><span class="sxs-lookup"><span data-stu-id="7a80a-113">**Errors**</span></span>  
 <span data-ttu-id="7a80a-114">로그 파일에 오류 및 정보 메시지만 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="7a80a-114">Writes only errors and informational messages to the log file.</span></span>  
  
 <span data-ttu-id="7a80a-115">**경고**</span><span class="sxs-lookup"><span data-stu-id="7a80a-115">**Warnings**</span></span>  
 <span data-ttu-id="7a80a-116">로그 파일에 경고 및 정보 메시지만 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="7a80a-116">Writes only warnings and informational messages to the log file.</span></span>  
  
 <span data-ttu-id="7a80a-117">**정보**</span><span class="sxs-lookup"><span data-stu-id="7a80a-117">**Information**</span></span>  
 <span data-ttu-id="7a80a-118">로그 파일에 정보 메시지만 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="7a80a-118">Writes only informational messages to the log file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a80a-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7a80a-119">See Also</span></span>  
 [<span data-ttu-id="7a80a-120">SQL Server 에이전트 오류 로그</span><span class="sxs-lookup"><span data-stu-id="7a80a-120">SQL Server Agent Error Log</span></span>](sql-server-agent-error-log.md)  
  
  
