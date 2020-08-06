---
title: LOGON 트리거 이벤트 데이터 캡처 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e05b1ab4-c10b-402a-9591-f6ec1e3db8c0
author: rothja
ms.author: jroth
ms.openlocfilehash: b11323702d7468d07783b4d1c763dba691479d9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660417"
---
# <a name="capture-logon-trigger-event-data"></a><span data-ttu-id="81ec8-102">LOGON 트리거 이벤트 데이터 캡처</span><span class="sxs-lookup"><span data-stu-id="81ec8-102">Capture Logon Trigger Event Data</span></span>
  <span data-ttu-id="81ec8-103">LOGON 트리거 내에서 사용할 LOGON 이벤트에 대한 XML 데이터를 캡처하려면 [EVENTDATA](/sql/t-sql/functions/eventdata-transact-sql) 함수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="81ec8-103">To capture XML data about LOGON events for use inside logon triggers, use the [EVENTDATA](/sql/t-sql/functions/eventdata-transact-sql) function.</span></span> <span data-ttu-id="81ec8-104">LOGON 이벤트는 다음 이벤트 데이터 스키마를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="81ec8-104">The LOGON event returns the following event data schema:</span></span>  
  
 `<EVENT_INSTANCE>`  
  
 `<EventType>event_type</EventType>`  
  
 `<PostTime>post_time</PostTime>`  
  
 `<SPID>spid</SPID>`  
  
 `<ServerName>server_name</ServerName>`  
  
 `<LoginName>login_name</LoginName>`  
  
 `<LoginType>login_type</LoginType>`  
  
 `<SID>sid</SID>`  
  
 `<ClientHost>client_host</ClientHost>`  
  
 `<IsPooled>is_pooled</IsPooled>`  
  
 `</EVENT_INSTANCE>`  
  
 `<EventType>`  
 <span data-ttu-id="81ec8-105">`LOGON`을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="81ec8-105">Contains `LOGON`.</span></span>  
  
 `<PostTime>`  
 <span data-ttu-id="81ec8-106">세션 설정이 요청된 시간을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="81ec8-106">Contains the time when a session is requested to be established.</span></span>  
  
 `<SID>`  
 <span data-ttu-id="81ec8-107">지정된 로그인 이름에 대한 SID(보안 ID)의 base 64로 인코딩된 이진 스트림을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="81ec8-107">Contains the base 64-encoded binary stream of the security identification number (SID) for the specified login name.</span></span>  
  
 `<ClientHost>`  
 <span data-ttu-id="81ec8-108">연결을 설정할 클라이언트의 호스트 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="81ec8-108">Contains the host name of the client from where the connection is made.</span></span> <span data-ttu-id="81ec8-109">클라이언트 이름과 서버 이름이 같을 경우 이 값은 '`<local_machine>`'입니다.</span><span class="sxs-lookup"><span data-stu-id="81ec8-109">The value is '`<local_machine>`' if the client and server name are the same.</span></span> <span data-ttu-id="81ec8-110">그렇지 않으면 값은 클라이언트의 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="81ec8-110">Otherwise, the value is the IP address of the client.</span></span>  
  
 `<IsPooled>`  
 <span data-ttu-id="81ec8-111">연결 풀링을 사용하여 연결이 다시 사용될 경우 `1` 입니다.</span><span class="sxs-lookup"><span data-stu-id="81ec8-111">Is `1` if the connection is reused by using connection pooling.</span></span> <span data-ttu-id="81ec8-112">그렇지 않으면 값은 `0`입니다.</span><span class="sxs-lookup"><span data-stu-id="81ec8-112">Otherwise, the value is `0`.</span></span>  
  
  
