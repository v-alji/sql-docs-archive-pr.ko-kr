---
title: FTP 태스크 편집기 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.general.f1
helpviewer_keywords:
- File Transfer Protocol Task Editor
ms.assetid: 28b46fdd-b04a-4f97-a99f-883f5735a6d9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0cb4ffe2fa44e76890f6b70912f84dbcaa8f2cd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648438"
---
# <a name="ftp-task-editor-general-page"></a><span data-ttu-id="131a0-102">FTP 태스크 편집기(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="131a0-102">FTP Task Editor (General Page)</span></span>
  <span data-ttu-id="131a0-103">**FTP 태스크 편집기** 대화 상자의 **일반** 페이지를 사용하여 태스크가 통신하는 FTP 서버에 연결하는 FTP 연결 관리자를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="131a0-103">Use the **General** page of the **FTP Task Editor** dialog box to specify the FTP connection manager that connects to the FTP server that the task communicates with.</span></span> <span data-ttu-id="131a0-104">또한 FTP 태스크를 명명 및 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="131a0-104">You can also name and describe the FTP task.</span></span>  
  
 <span data-ttu-id="131a0-105">이 태스크에 대한 자세한 내용은 [FTP 태스크](control-flow/ftp-task.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="131a0-105">To learn about this task, see [FTP Task](control-flow/ftp-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="131a0-106">옵션</span><span class="sxs-lookup"><span data-stu-id="131a0-106">Options</span></span>  
 <span data-ttu-id="131a0-107">**FtpConnection**</span><span class="sxs-lookup"><span data-stu-id="131a0-107">**FtpConnection**</span></span>  
 <span data-ttu-id="131a0-108">기존 FTP 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="131a0-108">Select an existing FTP connection manager, or click \<**New connection...**> to create a connection manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="131a0-109">FTP 연결 관리자는 익명 인증과 기본 인증만 지원하며</span><span class="sxs-lookup"><span data-stu-id="131a0-109">The FTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="131a0-110">Windows 인증은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="131a0-110">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="131a0-111">**관련 항목**: [FTP Connection Manager](connection-manager/ftp-connection-manager.md), [FTP Connection Manager Editor](../../2014/integration-services/ftp-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="131a0-111">**Related Topics**: [FTP Connection Manager](connection-manager/ftp-connection-manager.md), [FTP Connection Manager Editor](../../2014/integration-services/ftp-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="131a0-112">**StopOnFailure**</span><span class="sxs-lookup"><span data-stu-id="131a0-112">**StopOnFailure**</span></span>  
 <span data-ttu-id="131a0-113">FTP 작업이 실패할 경우 FTP 태스크가 종료될지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="131a0-113">Indicate whether the FTP task terminates if an FTP operation fails.</span></span>  
  
 <span data-ttu-id="131a0-114">**이름**</span><span class="sxs-lookup"><span data-stu-id="131a0-114">**Name**</span></span>  
 <span data-ttu-id="131a0-115">FTP 태스크에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="131a0-115">Provide a unique name for the FTP task.</span></span> <span data-ttu-id="131a0-116">이 이름은 태스크 아이콘에서 레이블로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="131a0-116">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="131a0-117">태스크 이름은 패키지 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="131a0-117">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="131a0-118">**설명**</span><span class="sxs-lookup"><span data-stu-id="131a0-118">**Description**</span></span>  
 <span data-ttu-id="131a0-119">FTP 태스크에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="131a0-119">Type a description of the FTP task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="131a0-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="131a0-120">See Also</span></span>  
 <span data-ttu-id="131a0-121">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="131a0-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="131a0-122">[FTP 태스크 편집기 &#40;파일 전송 페이지&#41;](../../2014/integration-services/ftp-task-editor-file-transfer-page.md) </span><span class="sxs-lookup"><span data-stu-id="131a0-122">[FTP Task Editor &#40;File Transfer Page&#41;](../../2014/integration-services/ftp-task-editor-file-transfer-page.md) </span></span>  
 [<span data-ttu-id="131a0-123">식 페이지</span><span class="sxs-lookup"><span data-stu-id="131a0-123">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
