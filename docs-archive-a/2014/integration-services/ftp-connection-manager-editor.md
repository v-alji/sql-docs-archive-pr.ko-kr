---
title: FTP 연결 관리자 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftpconnectionmanager.f1
helpviewer_keywords:
- FTP Connection Manager Editor
ms.assetid: 874b6585-255b-4a43-8396-bb08c3e8ac2b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d14635a4d90c267801f6d372dda5c7bcc7f4869f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743367"
---
# <a name="ftp-connection-manager-editor"></a><span data-ttu-id="95635-102">FTP 연결 관리자 편집기</span><span class="sxs-lookup"><span data-stu-id="95635-102">FTP Connection Manager Editor</span></span>
  <span data-ttu-id="95635-103">**FTP 연결 관리자 편집기** 대화 상자를 사용하여 FTP 서버 연결 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95635-103">Use the **FTP Connection Manager Editor** dialog box to specify properties for connecting to an FTP server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="95635-104">FTP 연결 관리자는 익명 인증과 기본 인증만 지원하며</span><span class="sxs-lookup"><span data-stu-id="95635-104">The FTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="95635-105">Windows 인증은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="95635-105">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="95635-106">FTP 연결 관리자에 대한 자세한 내용은 [FTP Connection Manager](connection-manager/ftp-connection-manager.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="95635-106">To learn more about the FTP connection manager, see [FTP Connection Manager](connection-manager/ftp-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="95635-107">옵션</span><span class="sxs-lookup"><span data-stu-id="95635-107">Options</span></span>  
 <span data-ttu-id="95635-108">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="95635-108">**Server name**</span></span>  
 <span data-ttu-id="95635-109">FTP 서버의 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="95635-109">Provide the name of the FTP server.</span></span>  
  
 <span data-ttu-id="95635-110">**서버 포트**</span><span class="sxs-lookup"><span data-stu-id="95635-110">**Server port**</span></span>  
 <span data-ttu-id="95635-111">연결에 사용할 FTP 서버의 포트 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95635-111">Specify the port number on the FTP server to use for the connection.</span></span> <span data-ttu-id="95635-112">이 속성의 기본값은 **21**입니다.</span><span class="sxs-lookup"><span data-stu-id="95635-112">The default value of this property is **21**.</span></span>  
  
 <span data-ttu-id="95635-113">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="95635-113">**User name**</span></span>  
 <span data-ttu-id="95635-114">FTP 서버에 액세스하기 위한 사용자 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="95635-114">Provide a user name to access the FTP server.</span></span> <span data-ttu-id="95635-115">이 속성의 기본값은 **anonymous**입니다.</span><span class="sxs-lookup"><span data-stu-id="95635-115">The default value of this property is **anonymous**.</span></span>  
  
 <span data-ttu-id="95635-116">**암호**</span><span class="sxs-lookup"><span data-stu-id="95635-116">**Password**</span></span>  
 <span data-ttu-id="95635-117">FTP 서버에 액세스하기 위한 암호를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="95635-117">Provide the password to access the FTP server.</span></span>  
  
 <span data-ttu-id="95635-118">**제한 시간(초)**</span><span class="sxs-lookup"><span data-stu-id="95635-118">**Time-out (in seconds)**</span></span>  
 <span data-ttu-id="95635-119">태스크가 시간 초과 될 때까지 걸리는 시간 (초)을 지정 합니다. 값 **0** 은 시간 제한이 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="95635-119">Specify the number of seconds the task takes before timing out. A value of **0** indicates an infinite amount of time.</span></span> <span data-ttu-id="95635-120">이 속성의 기본값은 **60**입니다.</span><span class="sxs-lookup"><span data-stu-id="95635-120">The default value of this property is **60**.</span></span>  
  
 <span data-ttu-id="95635-121">**Passive 모드 사용**</span><span class="sxs-lookup"><span data-stu-id="95635-121">**Use passive mode**</span></span>  
 <span data-ttu-id="95635-122">서버가 연결을 시작하는지 또는 클라이언트가 연결을 시작하는지 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95635-122">Specify whether the server or the client initiates the connection.</span></span> <span data-ttu-id="95635-123">서버는 Active 모드로 연결을 시작하고 클라이언트는 Passive 모드로 연결을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="95635-123">The server initiates the connection in active mode, and the client activates the connection in passive mode.</span></span> <span data-ttu-id="95635-124">이 속성의 기본값은 **active mode**입니다.</span><span class="sxs-lookup"><span data-stu-id="95635-124">The default value of this property is **active mode**.</span></span>  
  
 <span data-ttu-id="95635-125">**재시도**</span><span class="sxs-lookup"><span data-stu-id="95635-125">**Retries**</span></span>  
 <span data-ttu-id="95635-126">태스크가 연결하려고 하는 횟수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95635-126">Specify the number of times the task attempts to make a connection.</span></span> <span data-ttu-id="95635-127">값 **0** 은 시도 횟수에 제한이 없다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="95635-127">A value of **0** indicates no limit to the number of attempts.</span></span>  
  
 <span data-ttu-id="95635-128">**청크 크기(KB)**</span><span class="sxs-lookup"><span data-stu-id="95635-128">**Chunk size (in KB)**</span></span>  
 <span data-ttu-id="95635-129">데이터를 전송하기 위한 청크 크기(KB)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="95635-129">Provide a chunk size in kilobytes for transmitting data.</span></span>  
  
 <span data-ttu-id="95635-130">**연결 테스트**</span><span class="sxs-lookup"><span data-stu-id="95635-130">**Test Connection**</span></span>  
 <span data-ttu-id="95635-131">FTP 연결 관리자를 구성했으면 **연결 테스트**를 클릭하여 연결이 실행 가능한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="95635-131">After configuring the FTP Connection Manager, confirm that the connection is viable by clicking **Test Connection**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95635-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="95635-132">See Also</span></span>  
 [<span data-ttu-id="95635-133">Integration Services 오류 및 메시지 참조</span><span class="sxs-lookup"><span data-stu-id="95635-133">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
