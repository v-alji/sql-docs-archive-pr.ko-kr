---
title: SQL Server 에이전트 속성(일반 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.general.f1
ms.assetid: b51601e9-5454-43c6-bb5e-24eb2ff043c8
author: stevestein
ms.author: sstein
ms.openlocfilehash: a67d5431be4025c18b11d6791b016fa83e957810
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659774"
---
# <a name="sql-server-agent-properties-general-page"></a><span data-ttu-id="4e8da-102">SQL Server 에이전트 속성(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="4e8da-102">SQL Server Agent Properties (General Page)</span></span>
  <span data-ttu-id="4e8da-103">이 페이지를 사용 하 여 에이전트 서비스의 일반 속성을 확인 하 고 수정할 수 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e8da-103">Use this page to view and modify the general properties of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4e8da-104">옵션</span><span class="sxs-lookup"><span data-stu-id="4e8da-104">Options</span></span>  
 <span data-ttu-id="4e8da-105">**서비스 상태**</span><span class="sxs-lookup"><span data-stu-id="4e8da-105">**Service state**</span></span>  
 <span data-ttu-id="4e8da-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스의 현재 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4e8da-106">Displays the current state of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
 <span data-ttu-id="4e8da-107">**SQL Server가 갑자기 작동을 멈추면 자동으로 다시 시작**</span><span class="sxs-lookup"><span data-stu-id="4e8da-107">**Auto restart SQL Server if it stops unexpectedly**</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="4e8da-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 갑자기 중지되면 에이전트에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="4e8da-108">Agent restarts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stops unexpectedly.</span></span>  
  
 <span data-ttu-id="4e8da-109">**SQL Server 에이전트가 갑자기 작동을 멈추면 자동으로 다시 시작**</span><span class="sxs-lookup"><span data-stu-id="4e8da-109">**Auto restart SQL Server Agent if it stops unexpectedly**</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="4e8da-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 갑자기 중지되면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="4e8da-110">restarts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent stops unexpectedly.</span></span>  
  
 <span data-ttu-id="4e8da-111">**이름도**</span><span class="sxs-lookup"><span data-stu-id="4e8da-111">**Filename**</span></span>  
 <span data-ttu-id="4e8da-112">오류 로그 파일의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4e8da-112">Specify the file name for the error log.</span></span>  
  
 <span data-ttu-id="4e8da-113">**...**</span><span class="sxs-lookup"><span data-stu-id="4e8da-113">**...**</span></span>  
 <span data-ttu-id="4e8da-114">오류 로그 파일을 찾아봅니다.</span><span class="sxs-lookup"><span data-stu-id="4e8da-114">Browse to the error log file.</span></span>  
  
 <span data-ttu-id="4e8da-115">**실행 추적 메시지 포함**</span><span class="sxs-lookup"><span data-stu-id="4e8da-115">**Include execution trace messages**</span></span>  
 <span data-ttu-id="4e8da-116">오류 로그에 실행 추적 메시지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e8da-116">Includes execution trace messages in the error log.</span></span> <span data-ttu-id="4e8da-117">추적 메시지에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업에 대한 정보가 자세히 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e8da-117">Trace messages provide detailed information on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operation.</span></span> <span data-ttu-id="4e8da-118">따라서 이 옵션을 선택하면 로그 파일을 저장하는 데 디스크 공간이 더 많이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e8da-118">Therefore, the log file requires more disk space when this option is selected.</span></span> <span data-ttu-id="4e8da-119">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트와 관련한 문제를 해결하는 경우에만 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e8da-119">This option should only be selected while troubleshooting a problem that may involve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
 <span data-ttu-id="4e8da-120">**OEM 파일 쓰기**</span><span class="sxs-lookup"><span data-stu-id="4e8da-120">**Write OEM file**</span></span>  
 <span data-ttu-id="4e8da-121">오류 로그 파일을 비유니코드 파일로 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="4e8da-121">Writes the error log file as a non-Unicode file.</span></span> <span data-ttu-id="4e8da-122">이렇게 하면 로그 파일에서 사용하는 디스크 공간의 양이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="4e8da-122">This reduces the amount of disk space consumed by the log file.</span></span> <span data-ttu-id="4e8da-123">그러나 이 옵션을 설정하면 유니코드 데이터가 포함된 메시지를 읽기가 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e8da-123">However, messages that include Unicode data may be more difficult to read when this option is enabled.</span></span>  
  
 <span data-ttu-id="4e8da-124">**Net Send 수신자**</span><span class="sxs-lookup"><span data-stu-id="4e8da-124">**Net send recipient**</span></span>  
 <span data-ttu-id="4e8da-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 로그 파일에 작성한 메시지의 Net Send 알림을 수신할 운영자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4e8da-125">Type the name of an operator to receive net send notification of messages that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent writes to the log file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e8da-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4e8da-126">See Also</span></span>  
 <span data-ttu-id="4e8da-127">[작업자](operators.md) </span><span class="sxs-lookup"><span data-stu-id="4e8da-127">[Operators](operators.md) </span></span>  
 [<span data-ttu-id="4e8da-128">SQL Server 에이전트 오류 로그</span><span class="sxs-lookup"><span data-stu-id="4e8da-128">SQL Server Agent Error Log</span></span>](sql-server-agent-error-log.md)  
  
  
