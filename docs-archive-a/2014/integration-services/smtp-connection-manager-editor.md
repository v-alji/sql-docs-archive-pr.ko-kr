---
title: SMTP 연결 관리자 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.smtpconnection.f1
helpviewer_keywords:
- SMTP Connection Manager Editor
ms.assetid: 2693de0d-b04d-4325-a856-ce667d2b8aa1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e14ed49f64b9faca40f575fc6760a8d25c0d4573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742348"
---
# <a name="smtp-connection-manager-editor"></a><span data-ttu-id="93212-102">SMTP 연결 관리자 편집기</span><span class="sxs-lookup"><span data-stu-id="93212-102">SMTP Connection Manager Editor</span></span>
  <span data-ttu-id="93212-103">**SMTP 연결 관리자 편집기** 대화 상자를 사용하여 SMTP(Simple Mail Transfer Protocol) 서버를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93212-103">Use the **SMTP Connection Manager Editor** dialog box to specify a Simple Mail Transfer Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="93212-104">SMTP 연결 관리자에 대한 자세한 내용은 [SMTP Connection Manager](connection-manager/smtp-connection-manager.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="93212-104">To learn more about the SMTP connection manager, see [SMTP Connection Manager](connection-manager/smtp-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="93212-105">옵션</span><span class="sxs-lookup"><span data-stu-id="93212-105">Options</span></span>  
 <span data-ttu-id="93212-106">**이름**</span><span class="sxs-lookup"><span data-stu-id="93212-106">**Name**</span></span>  
 <span data-ttu-id="93212-107">연결 관리자의 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="93212-107">Provide a unique name for the connection manager.</span></span>  
  
 <span data-ttu-id="93212-108">**설명**</span><span class="sxs-lookup"><span data-stu-id="93212-108">**Description**</span></span>  
 <span data-ttu-id="93212-109">연결 관리자에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="93212-109">Describe the connection manager.</span></span> <span data-ttu-id="93212-110">설명에 해당 연결 관리자의 용도를 정의하면 패키지를 이해하기 쉬우며 유지 관리가 간편합니다.</span><span class="sxs-lookup"><span data-stu-id="93212-110">As a best practice, describe the connection manager in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="93212-111">**SMTP 서버**</span><span class="sxs-lookup"><span data-stu-id="93212-111">**SMTP server**</span></span>  
 <span data-ttu-id="93212-112">SMTP 서버의 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="93212-112">Provide the name of the SMTP server.</span></span>  
  
 <span data-ttu-id="93212-113">**Windows 인증 사용**</span><span class="sxs-lookup"><span data-stu-id="93212-113">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="93212-114">Windows 인증을 통해 서버에 대한 액세스를 인증하는 SMTP 서버를 사용하여 메일을 보내려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="93212-114">Select to send mail using an SMTP server that uses Windows Authentication to authenticate access to the server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="93212-115">SMTP 연결 관리자는 익명 인증과 Windows 인증만 지원하며</span><span class="sxs-lookup"><span data-stu-id="93212-115">The SMTP connection manager supports only anonymous authentication and Windows Authentication.</span></span> <span data-ttu-id="93212-116">기본 인증은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93212-116">It does not support basic authentication.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93212-117">Microsoft Exchange를 SMTP 서버로 사용 하는 경우 **Windows 인증 사용** 을로 설정 해야 할 수 있습니다 `True` .</span><span class="sxs-lookup"><span data-stu-id="93212-117">When using Microsoft Exchange as the SMTP server, you may need to set **Use Windows Authentication** to `True`.</span></span> <span data-ttu-id="93212-118">인증되지 않은 SMTP 연결을 허용하지 않도록 Exchange Server를 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93212-118">Exchange servers may be configured to disallow unauthenticated SMTP connections.</span></span>  
  
 <span data-ttu-id="93212-119">**SSL(Secure Sockets Layer) 사용**</span><span class="sxs-lookup"><span data-stu-id="93212-119">**Enable Secure Sockets Layer (SSL)**</span></span>  
 <span data-ttu-id="93212-120">전자 메일 메시지를 보낼 때 SSL(Secure Sockets Layer)을 사용하여 통신을 암호화하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="93212-120">Select to encrypt communication using Secure Sockets Layer (SSL) when sending e-mail messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93212-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="93212-121">See Also</span></span>  
 [<span data-ttu-id="93212-122">Integration Services 오류 및 메시지 참조</span><span class="sxs-lookup"><span data-stu-id="93212-122">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
